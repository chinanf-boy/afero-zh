# spf13/afero [![translate-svg]][translate-list]

<!--[![explain]][source]-->

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list

「 Go 的文件系统抽象系统 」

[中文](./readme.md) | [english](https://github.com/spf13/afero)

---

## 校对 ✅

<!-- doc-templite START generated -->
<!-- repo = 'spf13/afero' -->
<!-- commit = 'd40851caa0d747393da1ffb28f7f9d8b4eeffebd' -->
<!-- time = '2018-09-07' -->

| 翻译的原文 | 与日期        | 最新更新 | 更多                       |
| ---------- | ------------- | -------- | -------------------------- |
| [commit]   | ⏰ 2018-09-07 | ![last]  | [中文翻译][translate-list] |

[last]: https://img.shields.io/github/last-commit/spf13/afero.svg
[commit]: https://github.com/spf13/afero/tree/d40851caa0d747393da1ffb28f7f9d8b4eeffebd

<!-- doc-templite END generated -->

### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

---

![afero logo-sm](https://cloud.githubusercontent.com/assets/173412/11490338/d50e16dc-97a5-11e5-8b12-019a300d0fcb.png)

Go 的文件系统抽象系统

[![Build Status](https://travis-ci.org/spf13/afero.svg)](https://travis-ci.org/spf13/afero) [![Build status](https://ci.appveyor.com/api/projects/status/github/spf13/afero?branch=master&svg=true)](https://ci.appveyor.com/project/spf13/afero) [![GoDoc](https://godoc.org/github.com/spf13/afero?status.svg)](https://godoc.org/github.com/spf13/afero) [![Join the chat at https://gitter.im/spf13/afero](https://badges.gitter.im/Dev%20Chat.svg)](https://gitter.im/spf13/afero?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

### 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [概观](#%E6%A6%82%E8%A7%82)
  - [Afero 特性](#afero-%E7%89%B9%E6%80%A7)
- [使用 Afero](#%E4%BD%BF%E7%94%A8-afero)
  - [第 1 步:安装 Afero](#%E7%AC%AC-1-%E6%AD%A5%E5%AE%89%E8%A3%85-afero)
  - [第 2 步:声明后端](#%E7%AC%AC-2-%E6%AD%A5%E5%A3%B0%E6%98%8E%E5%90%8E%E7%AB%AF)
  - [第 3 步:像操作系统包一样使用它](#%E7%AC%AC-3-%E6%AD%A5%E5%83%8F%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%E5%8C%85%E4%B8%80%E6%A0%B7%E4%BD%BF%E7%94%A8%E5%AE%83)
  - [所有可用功能的列表](#%E6%89%80%E6%9C%89%E5%8F%AF%E7%94%A8%E5%8A%9F%E8%83%BD%E7%9A%84%E5%88%97%E8%A1%A8)
  - [使用 Afero 的实用功能](#%E4%BD%BF%E7%94%A8-afero-%E7%9A%84%E5%AE%9E%E7%94%A8%E5%8A%9F%E8%83%BD)
    - [直接调用实用程序](#%E7%9B%B4%E6%8E%A5%E8%B0%83%E7%94%A8%E5%AE%9E%E7%94%A8%E7%A8%8B%E5%BA%8F)
    - [通过 Afero 调用](#%E9%80%9A%E8%BF%87-afero-%E8%B0%83%E7%94%A8)
  - [使用 Afero 进行测试](#%E4%BD%BF%E7%94%A8-afero-%E8%BF%9B%E8%A1%8C%E6%B5%8B%E8%AF%95)
- [可用的后端](#%E5%8F%AF%E7%94%A8%E7%9A%84%E5%90%8E%E7%AB%AF)
  - [原生操作系统](#%E5%8E%9F%E7%94%9F%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F)
    - [OsFs](#osfs)
  - [内存支持存储](#%E5%86%85%E5%AD%98%E6%94%AF%E6%8C%81%E5%AD%98%E5%82%A8)
    - [MemMapFs](#memmapfs)
      - [InMemoryFile](#inmemoryfile)
  - [网络接口](#%E7%BD%91%E7%BB%9C%E6%8E%A5%E5%8F%A3)
    - [SftpFs](#sftpfs)
  - [过滤后端](#%E8%BF%87%E6%BB%A4%E5%90%8E%E7%AB%AF)
    - [BasePathFs](#basepathfs)
    - [ReadOnlyFs](#readonlyfs)
- [RegexpFs](#regexpfs)
    - [HttpFs](#httpfs)
  - [复合后端](#%E5%A4%8D%E5%90%88%E5%90%8E%E7%AB%AF)
    - [CacheOnReadFs](#cacheonreadfs)
    - [CopyOnWriteFs()](#copyonwritefs)
  - [期望/可能的后端](#%E6%9C%9F%E6%9C%9B%E5%8F%AF%E8%83%BD%E7%9A%84%E5%90%8E%E7%AB%AF)
- [关于该项目](#%E5%85%B3%E4%BA%8E%E8%AF%A5%E9%A1%B9%E7%9B%AE)
  - [这个名字是什么](#%E8%BF%99%E4%B8%AA%E5%90%8D%E5%AD%97%E6%98%AF%E4%BB%80%E4%B9%88)
  - [发行说明](#%E5%8F%91%E8%A1%8C%E8%AF%B4%E6%98%8E)
  - [贡献](#%E8%B4%A1%E7%8C%AE)
  - [贡献者](#%E8%B4%A1%E7%8C%AE%E8%80%85)
  - [执照](#%E6%89%A7%E7%85%A7)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 概观

Afero 是一个文件系统框架,提供与任何文件系统的简单,统一和通用的交互 API。作为提供接口,类型和方法的抽象层，Afero 具有非常干净的接口和简单的设计,没有不必要的构造函数或初始化方法。

Afero 也是一个库,提供一组可互操作的后端文件系统,轻松地使用。同时保留 os 和 ioutil 包的所有功能和优点.

Afero 比单独使用 os 包提供了显着的改进,最显着的是能够在不依赖磁盘的情况下，创建模拟和测试文件系统.

它考虑到了，您想使用 OS 包的任何情况,因为它提供了额外的抽象,使得在测试期间可以轻松使用内存支持的文件系统。它还增加了对 http 文件系统的支持,以实现完全的互操作性.

## Afero 特性

- 用于访问各种文件系统的唯一的一致 API
- 各种文件系统类型之间的互操作
- 一组接口,用于鼓励，和实现后端之间的互操作性
- 跨平台内存支持的文件原子系统
- 通过组合多个文件系统，来支持一个组合(联合)文件系统
- 修改现有文件系统的专用后端(只读,Regexp 过滤)
- 一组从 io,ioutil 和 hugo 移植到 afero 意识的实用函数

# 使用 Afero

Afero 易于使用，且简单明了.

您可以使用 Afero 的几种不同方式:

- 单独使用接口，来定义您自己的文件系统.
- 包装为 OS 包.
- 为应用程序的不同部分，定义不同的文件系统.
- 在测试时，使用 Afero 模拟文件系统

## 第 1 步:安装 Afero

首先使用 go get 安装最新版本的库.

```
$ go get github.com/spf13/afero
```

接下来在您的应用程序中，包含 Afero.

```go
import "github.com/spf13/afero"
```

## 第 2 步:声明后端

首先定义一个包级变量，并将其设置为指向文件系统的指针.

```go
var AppFs = afero.NewMemMapFs()

or

var AppFs = afero.NewOsFs()
```

重要的是要注意,如果重复调用，您将使用一个全新的隔离文件系统。在 OsFs 的情况下,它仍将使用相同的底层文件系统，但会降低根据需要放入其他文件系统的能力.

## 第 3 步:像操作系统包一样使用它

在整个应用程序中,使用您通常会使用的任何功能和方法.

所以,如果我以前的应用有:

```go
os.Open('/tmp/foo')
```

我们将其替换为:

```go
AppFs.Open('/tmp/foo')
```

`AppFs`是我们上面定义的变量.

## 所有可用功能的列表

文件系统方法可用:

```go
Chmod(name string, mode os.FileMode) : error
Chtimes(name string, atime time.Time, mtime time.Time) : error
Create(name string) : File, error
Mkdir(name string, perm os.FileMode) : error
MkdirAll(path string, perm os.FileMode) : error
Name() : string
Open(name string) : File, error
OpenFile(name string, flag int, perm os.FileMode) : File, error
Remove(name string) : error
RemoveAll(path string) : error
Rename(oldname, newname string) : error
Stat(name string) : os.FileInfo, error
```

文件接口和方法可用:

```go
io.Closer
io.Reader
io.ReaderAt
io.Seeker
io.Writer
io.WriterAt

Name() : string
Readdir(count int) : []os.FileInfo, error
Readdirnames(n int) : []string, error
Stat() : os.FileInfo, error
Sync() : error
Truncate(size int64) : error
WriteString(s string) : ret int, err error
```

在某些应用程序中,定义一个只导出**文件系统变量**的新包，就可以从任何地方轻松访问。

## 使用 Afero 的实用功能

Afero 提供了一组函数,使其更易于使用底层文件系统。这些函数主要来自 io&ioutil,其中一些是为 Hugo 开发的.

afero 实用程序，支持所有 afero 兼容的后端.

实用程序列表包括:

```go
DirExists(path string) (bool, error)
Exists(path string) (bool, error)
FileContainsBytes(filename string, subslice []byte) (bool, error)
GetTempDir(subPath string) string
IsDir(path string) (bool, error)
IsEmpty(path string) (bool, error)
ReadDir(dirname string) ([]os.FileInfo, error)
ReadFile(filename string) ([]byte, error)
SafeWriteReader(path string, r io.Reader) (err error)
TempDir(dir, prefix string) (name string, err error)
TempFile(dir, prefix string) (f File, err error)
Walk(root string, walkFn filepath.WalkFunc) error
WriteFile(filename string, data []byte, perm os.FileMode) error
WriteReader(path string, r io.Reader) (err error)
```

有关完整列表,请参阅[Afero 的 GoDoc](https://godoc.org/github.com/spf13/afero)

这里是有两种不同的使用方法。

- 您可以直接调用它们,每个函数的第一个参数将是文件系统,或者

- 您可以声明一个新`Afero`,一种自定义类型,用于将这些函数绑定到，给定文件系统的方法.

### 直接调用实用程序

```go
fs := new(afero.MemMapFs)
f, err := afero.TempFile(fs,"", "ioutil-test")
```

### 通过 Afero 调用

```go
fs := afero.NewMemMapFs()
afs := &afero.Afero{Fs: fs}
f, err := afs.TempFile("", "ioutil-test")
```

## 使用 Afero 进行测试

使用模拟文件系统进行测试有很大好处。每次初始化时，它都处于完全空白状态,无论操作系统如何,都可以轻松重现。您可以创建重要内容文件,文件访问速度快,同时还可以避免，删除临时文件,Windows 文件锁定等所有烦人的问题。MemMapFs 后端非常适合测试.

- 比在磁盘上执行 I/O 操作快得多
- 避免安全和权限问题
- 更多的控制。'rm -rf /'将充满信心
- 测试设置要容易得多
- 无需进行测试清理

实现此目的的一种方法是定义如上所述的变量。在您的应用程序测试期间，这将被设置为`afero.NewOsFs()`，当然您也可以设为 `afero.NewMemMapFs()`.

每个测试都初始化一个空白的平板内存后端并不少见。要做到这一点, 在我应用程序代码中适当的地方，定义`appFS = afero.NewOsFs()`。此方法可确保测试与顺序无关,并且没有依赖于早期测试留下的状态.

然后在我的测试中,我会为每个测试初始化一个新的 MemMapF:

```go
func TestExist(t *testing.T) {
	appFS := afero.NewMemMapFs()
	// 创建 test 文件 和 目录
	appFS.MkdirAll("src/a", 0755)
	afero.WriteFile(appFS, "src/a/b", []byte("file b"), 0644)
	afero.WriteFile(appFS, "src/c", []byte("file c"), 0644)
	name := "src/c"
	_, err := appFS.Stat(name)
	if os.IsNotExist(err) {
		t.Errorf("file \"%s\" does not exist.\n", name)
	}
}
```

# 可用的后端

## 原生操作系统

### OsFs

第一个是围绕原生 OS 调用的包装器。将它变得非常容易使用,因为所有调用都与现有的 OS 调用相同。它还使您的代码在操作系统，与根据需要使用模拟文件系统时，变得轻松，甚至*无聊^\_^*。

```go
appfs := afero.NewOsFs()
appfs.MkdirAll("src/a", 0755))
```

## 内存支持存储

### MemMapFs

Afero 还提供完全原子内存支持的文件系统,非常适合用于模拟,并在不需要保持时，加速不必要的磁盘。它是完全并发的,可以安全地在 go 协程中使用.

```go
mm := afero.NewMemMapFs()
mm.MkdirAll("src/a", 0755))
```

#### InMemoryFile

作为 MemMapFs 的一部分,Afero 还提供原子的,完全并发的内存支持文件实现.这可以轻松地在其他内存支持的文件系统中使用.计划是使用 InMemoryFile 添加基数树内存存储文件系统.

## 网络接口

### SftpFs

Afero 对安全文件传输协议(sftp)有实验性的支持。可用于加密通道上执行文件操作.

## 过滤后端

### BasePathFs

BasePathF 将所有操作限制在 Fs 内的给定路径。在调用这个源 Fs 之前, Fs 操作的给定文件名，会以基本路径为前缀.

```go
bp := afero.NewBasePathFs(afero.NewOsFs(), "/base/path")
```

### ReadOnlyFs

源 Fs 周围的薄包装器,提供只读的.

```go
fs := afero.NewReadOnlyFs(afero.NewOsFs())
_, err := fs.Create("/file.txt")
// err = syscall.EPERM
```

# RegexpFs

对文件名进行过滤后的,任何与传递的正则表达式不匹配的文件，都将被视为不存在。将不会创建与提供的正则表达式不匹配的文件。目录不过滤.

```go
fs := afero.NewRegexpFs(afero.NewMemMapFs(), regexp.MustCompile(`\.txt$`))
_, err := fs.Create("/file.html")
// err = syscall.ENOENT
```

### HttpFs

Afero 提供了一个 http 兼容的后端,可以包装任何现有的后端.

Http 包需要稍微特定的 Open 版本,它返回一个 http.File 类型.

Afero 提供满足此要求的 httpFs 文件系统。任何 Afero FileSystem 都可以用作 httpFs。

```go
httpFs := afero.NewHttpFs(<ExistingFS>)
fileserver := http.FileServer(httpFs.Dir(<PATH>)))
http.Handle("/", fileserver)
```

## 复合后端

Afero 提供合成两个文件系统(或更多)，作为单个文件系统的能力.

### CacheOnReadFs

CacheOnReadFs 将懒洋洋地将任何访问过的文件，从`基础层-base`复制到`覆盖层-overlay`中。后续读取将直接从覆盖层中提取，允许缓存持续时间内，请求在覆盖层中创建的缓存。

如果基本文件系统是可写的,则对文件的任何更改，将首先对基础层进行,然后对覆盖层进行。而打开文件的 Write 调用控制,如`Write()`或`Truncate()`则先到覆盖层.

要仅将文件写入覆盖层,可以直接使用覆盖层 Fs(而不是通过联合 Fs).

在给定`time.Duration`缓存持续时间内，对该层中的文件进行缓存，缓存持续时间为 0 ，意味着"永远"，意味着文件将不会从基础层重新请求.

只读的基础层会让覆盖层也是只读的，但是当文件在缓存层中不存在(或过时)时，仍然将文件从基础层复制到覆盖层.

```go
base := afero.NewOsFs()
layer := afero.NewMemMapFs()
ufs := afero.NewCacheOnReadFs(base, layer, 100 * time.Second)
```

### CopyOnWriteFs()

CopyOnWriteFs 是一个只读的基本文件系统,顶部有一个可写的层.

Read 操作首先查看覆盖层,如果没有找到,将从基础层提供文件服务.

只能在覆盖层中对文件系统进行更改.

任何仅在基础中找到的文件的修改，都会在修改(包括打开可写的文件)之前，将文件复制到覆盖层.

目前不允许删除和重命名，仅存在于基础层中的文件。如果文件在基础层和覆盖层中存在,则仅能删除/重命名覆盖层.

```go
	base := afero.NewOsFs()
	roBase := afero.NewReadOnlyFs(base)
	ufs := afero.NewCopyOnWriteFs(roBase, afero.NewMemMapFs())

	fh, _ = ufs.Create("/home/test/file2.txt")
	fh.WriteString("This is a test")
	fh.Close()
```

在此示例中,所有写入操作仅发生在内存(MemMapFs)中, 基本文件系统(OsFs)保持不变.

## 期望/可能的后端

以下是我们希望有人可能实现的后端，简短列表:

- SSH
- ZIP
- TAR
- S3

# 关于该项目

## 这个名字是什么

Afero 来自拉丁美洲的 Ad-Facere.

**"Ad"**是一个前缀,意思是"to".

**"Facere"**是"make 或 do "的根单词"faciō"的一种形式.

afero 的字面含义是"to make"或"to do",这对于允许制作文件和目录,并使用它们进行操作的库来说非常合适.

与 Afero 具有相同根源的英语单词是"affair"。Affair 拥有相同的概念,但作为名词,它意味着"制造或完成的东西"或"特定类型的物体".

与我的其他一些库(hugo,cobra,viper)不同,谷歌一下也不错.

## 发行说明

- **0.10.0** 2015.12.10
  - 与 Windows 完全兼容
  - 介绍 afero 实用函数
  - 测试套件重写，为跨平台工作
  - 规范化 MemMapFs 的路径
  - 将 Sync 添加到文件接口
  - **破而后立** Walk 和 ReadDir 已更改参数顺序
  - 将 MemMapFs 使用的类型移动到子包中
  - 一般错误修正和改进
- **0.9.0** 2015.11.05
  - 新的 Walk 函数类似于 filepath.Walk
  - MemMapFs.OpenFile 处理 O_CREATE,O_APPEND,O_TRUNC
  - MemMapFs.Remove 现在真的删除了该文件
  - InMemoryFile.Readdir 和 Readdirnames 正常工作
  - InMemoryFile 函数将其锁定以进行并发访问
  - 测试套件改进
- **0.8.0** 2014.10.28
  - 第一个公开版
  - 接口感觉准备好，为人们构建使用
  - 接口满足所有已知用途
  - MemMapFs 通过了大部分 OS 测试套件
  - OsFs 通过了大部分 OS 测试套件

## 贡献

1.  叉-Fork 吧
2.  创建您的功能分支(`git checkout -b my-new-feature`)
3.  提交你的更改(`git commit -am 'Add some feature'`)
4.  推到分支(`git push origin my-new-feature`)
5.  创建新的 Pull 请求

## 贡献者

名字没有特别的顺序:

- [spf13](https://github.com/spf13)
- [jaqx0r](https://github.com/jaqx0r)
- [mbertschler](https://github.com/mbertschler)
- [XOR 门](https://github.com/xor-gate)

## 执照

Afero 是在 Apache 2.0 许可下发布的。看到[LICENSE.txt](https://github.com/spf13/afero/blob/master/LICENSE.txt)
