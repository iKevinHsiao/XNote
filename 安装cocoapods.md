[toc]

> 系统版本： macOS Catalina 10.15.7
>
> [ruby-china](https://gems.ruby-china.com/)
>
> 本文档非使用Homebrew

#### 1、查看当前Ruby环境

```shell
$ gem -v
3.0.3
```



#### 2、升级Ruby环境

> 没有权限的方式

```shell
# 输入
$ gem update --system

# 输出
Updating rubygems-update
^[[AFetching rubygems-update-3.2.20.gem
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.
```



> 使用超级权限升级ruby

```shell
# 输入
$ sudo gem update --system

# 输入密码
Password:

# 输出
Updating rubygems-update
Fetching rubygems-update-3.2.20.gem
Successfully installed rubygems-update-3.2.20
Parsing documentation for rubygems-update-3.2.20
Installing ri documentation for rubygems-update-3.2.20
Installing darkfish documentation for rubygems-update-3.2.20
Done installing documentation for rubygems-update after 221 seconds
Parsing documentation for rubygems-update-3.2.20
Done installing documentation for rubygems-update after 0 seconds
Installing RubyGems 3.2.20
ERROR:  While executing gem ... (Errno::EPERM)
    Operation not permitted @ rb_sysopen - /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/bin/gem
```



> 再次查看版本

```shell
# 输入
$ gem -v

# 输出
3.2.20
```



#### 3、替换Ruby镜像

```shell
# 将默认源替换成 https://gems.ruby-china.com/
$ gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/

# 查看源列表 确保只有 gems.ruby-china.com
$ gem sources -l
https://gems.ruby-china.com
```



#### 4、安装cocoapods

##### 4.1、安装指令

```shell
$ sudo gem install cocoapods
```



##### 4.2、查看版本

```shell
$ pod --version
1.10.1
```



##### 4.3、初始化

> 应该在这之前设置仓库，否则会出现4.5的问题

```shell
$ pod setup    
Setup completed
```



##### 4.4、搜索第三方库

```shell
$ pod search afnetworking
```



##### 4.5、如果搜索第三方库失败

> 报错

```shell
$ pod search afnetworking
Setup completed
[!] Unable to find a pod with name, author, summary, or description matching `afnetworking`
```

> 解决方法：给pod设置仓库

```shell
$ pod repo add master https://github.com/CocoaPods/Specs.git
```

如果这一步卡在

```shell
Cloning spec repo `master` from `https://github.com/CocoaPods/Specs.git`
```

可以在`活动监视器` - `网络`找到`git-remote-https`查看文件大小





##### 4.6、如果安装失败 找不到ffi

> 如果报错了，根据错误提示解决

```shell
# 输入
sudo gem install cocoapods

# 密码
Password:
Fetching nanaimo-0.3.0.gem
Fetching colored2-3.1.2.gem
Fetching claide-1.0.3.gem
Fetching atomos-0.1.3.gem
Fetching xcodeproj-1.19.0.gem
Fetching ruby-macho-1.4.0.gem
Fetching nap-1.1.0.gem
Fetching molinillo-0.6.6.gem
Fetching gh_inspector-1.1.3.gem
Fetching fourflusher-2.3.1.gem
Fetching escape-0.0.4.gem
Fetching cocoapods-try-1.2.0.gem
Fetching netrc-0.11.0.gem
Fetching cocoapods-trunk-1.5.0.gem
Fetching cocoapods-search-1.0.0.gem
Fetching cocoapods-plugins-1.0.0.gem
Fetching cocoapods-downloader-1.4.0.gem
Fetching cocoapods-deintegrate-1.0.4.gem
Fetching ffi-1.15.3.gem
Fetching ethon-0.14.0.gem
Fetching typhoeus-1.4.0.gem
Fetching public_suffix-4.0.6.gem
Fetching fuzzy_match-2.0.4.gem
Fetching concurrent-ruby-1.1.9.gem
Fetching httpclient-2.8.3.gem
Fetching algoliasearch-1.27.5.gem
Fetching addressable-2.7.0.gem
Fetching thread_safe-0.3.6.gem
Fetching tzinfo-1.2.9.gem
Fetching i18n-1.8.10.gem
Fetching activesupport-5.2.6.gem
Fetching cocoapods-core-1.10.1.gem
Fetching cocoapods-1.10.1.gem
Successfully installed nanaimo-0.3.0
Successfully installed colored2-3.1.2
Successfully installed claide-1.0.3
Successfully installed atomos-0.1.3
Successfully installed xcodeproj-1.19.0
Successfully installed ruby-macho-1.4.0
Successfully installed nap-1.1.0
Successfully installed molinillo-0.6.6
Successfully installed gh_inspector-1.1.3
Successfully installed fourflusher-2.3.1
Successfully installed escape-0.0.4
Successfully installed cocoapods-try-1.2.0
Successfully installed netrc-0.11.0
Successfully installed cocoapods-trunk-1.5.0
Successfully installed cocoapods-search-1.0.0
Successfully installed cocoapods-plugins-1.0.0
Successfully installed cocoapods-downloader-1.4.0
Successfully installed cocoapods-deintegrate-1.0.4
Building native extensions. This could take a while...
ERROR:  Error installing cocoapods:
	ERROR: Failed to build gem native extension.

    current directory: /Library/Ruby/Gems/2.6.0/gems/ffi-1.15.3/ext/ffi_c
/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/bin/ruby -I /Library/Ruby/Site/2.6.0 -r ./siteconf20210623-28937-13ko6hx.rb extconf.rb
checking for ffi.h... *** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.

Provided configuration options:
	--with-opt-dir
	--without-opt-dir
	--with-opt-include
	--without-opt-include=${opt-dir}/include
	--with-opt-lib
	--without-opt-lib=${opt-dir}/lib
	--with-make-prog
	--without-make-prog
	--srcdir=.
	--curdir
	--ruby=/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/bin/$(RUBY_BASE_NAME)
	--with-ffi_c-dir
	--without-ffi_c-dir
	--with-ffi_c-include
	--without-ffi_c-include=${ffi_c-dir}/include
	--with-ffi_c-lib
	--without-ffi_c-lib=${ffi_c-dir}/lib
	--enable-system-libffi
	--disable-system-libffi
	--with-libffi-config
	--without-libffi-config
	--with-pkg-config
	--without-pkg-config
/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:467:in `try_do': The compiler failed to generate an executable file. (RuntimeError)
You have to install development tools first.
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:585:in `block in try_compile'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:534:in `with_werror'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:585:in `try_compile'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:1109:in `block in have_header'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:959:in `block in checking_for'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:361:in `block (2 levels) in postpone'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:331:in `open'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:361:in `block in postpone'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:331:in `open'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:357:in `postpone'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:958:in `checking_for'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/mkmf.rb:1108:in `have_header'
	from extconf.rb:10:in `system_libffi_usable?'
	from extconf.rb:42:in `<main>'

To see why this extension failed to compile, please check the mkmf.log which can be found here:

  /Library/Ruby/Gems/2.6.0/extensions/universal-darwin-19/2.6.0/ffi-1.15.3/mkmf.log

extconf failed, exit code 1

Gem files will remain installed in /Library/Ruby/Gems/2.6.0/gems/ffi-1.15.3 for inspection.
Results logged to /Library/Ruby/Gems/2.6.0/extensions/universal-darwin-19/2.6.0/ffi-1.15.3/gem_make.out
```



> 查看错误日志地址
>
> `/Library/Ruby/Gems/2.6.0/extensions/universal-darwin-19/2.6.0/ffi-1.15.3/mkmf.log`

###### 报错原因

###### **package configuration for libffi is not found**

```shell
package configuration for libffi is not found

"xcrun clang -o conftest -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.1.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/include/ruby-2.6.0/universal-darwin19 -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.1.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/include/ruby-2.6.0/ruby/backward -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.1.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/include/ruby-2.6.0 -I. -D_XOPEN_SOURCE -D_DARWIN_C_SOURCE -D_DARWIN_UNLIMITED_SELECT -D_REENTRANT    -g -Os -pipe -DHAVE_GCC_ATOMIC_BUILTINS conftest.c  -L. -L/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib -L. -L/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.15.Internal.sdk/usr/local/lib   -arch x86_64   -lruby.2.6   "
In file included from conftest.c:1:
In file included from /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.1.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/include/ruby-2.6.0/ruby.h:33:
/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.1.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/include/ruby-2.6.0/ruby/ruby.h:24:10: fatal error: 'ruby/config.h' file not found
#include "ruby/config.h"
         ^~~~~~~~~~~~~~~
/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.1.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/include/ruby-2.6.0/ruby/ruby.h:24:10: note: did not find header 'config.h' in framework 'ruby' (loaded from '/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/System/Library/Frameworks')
1 error generated.
checked program was:
/* begin */
1: #include "ruby.h"
2: 
3: int main(int argc, char **argv)
4: {
5:   return 0;
6: }
/* end */
```

指的是这个文件`/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.1.sdk/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/include/ruby-2.6.0/ruby/ruby.h`中`#includ "ruby/config.h"`文件找不到。**该文件所在的上级目录`ruby`同级包含`universal-darwin20`**，**但是运行的指令执行的是`universal-darwin19`里的代码**

###### 解决方法

* 拷贝`universal-darwin20` 并重命名为`universal-darwin19`

* 再次执行安装命令

