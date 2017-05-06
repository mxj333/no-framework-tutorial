[下一篇>>](02-composer.md)

### 前端控制器

一个 [前端控制器](http://en.wikipedia.org/wiki/Front_Controller_pattern) 是进入您的应用程序的一个点。

要开始，为项目创建一个空目录。您还需要一个所有请求将进入的入口点。这意味着你必须创建一个`index.php`文件。

一个常见的方法是`index.php`将项目的根文件夹放在。这也是一些框架的做法。让我解释为什么你不应该这样做。

这`index.php`是起点，所以它必须在Web服务器目录中。这意味着Web服务器可以访问所有子目录。如果您正确设置，您仍然可以阻止它访问应用程序文件所在的子文件夹。

但有时候事情根本不会计划。如果出现问题，您的文件设置如上，您的整个应用程序源代码可能会暴露给访问者。我不必解释为什么这不是一件好事。

所以，而不是这样做，在你的项目文件夹中创建一个文件夹`public`。这是为应用程序创建`src`文件夹的好时机，也是在项目根文件夹中。

`public`您可以在文件夹中创建您的文件`index.php`。请记住，您不想在此处显示任何内容，因此只需将以下代码放在其中：


```php
<?php declare(strict_types = 1); 

require __DIR__ . '/../src/Bootstrap.php';
```

`__DIR__`是包含目录路径的[魔术常数](http://php.net/manual/en/language.constants.predefined.php)。通过使用它，您可以确保`require`始终使用与使用的文件相同的相对路径。否则，如果您`index.php`从不同的文件夹调用它将找不到该文件。

`declare(strict_types = 1);` 将当前文件设置为[严格打字](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict)。在本教程中，我们将使用所有PHP文件。这意味着您不能将整数作为参数传递给需要字符串的方法。如果不使用严格模式，它将被自动转换为所需类型。使用严格的模式，如果是错误的类型，它将抛出异常。

这 `Bootstrap.php` 将是将应用程序连接在一起的文件。我们很快就会到。

公用文件夹的其余部分保留给您的公共资产文件（如JavaScript文件和样式表）。

现在，在您的`src`文件夹内导航，并创建一个`Bootstrap.php`包含以下内容的新文件：

```php
<?php declare(strict_types = 1);

echo 'Hello World!';
```

现在我们来看看一切是否正确设置。打开控制台并导航到您的项目`public`文件夹。在那里键入`php -S localhost:8000`，然后按回车。这将启动内置的Web服务器，您可以在浏览器中访问您的页面`http://localhost:8000`。你现在应该看到'Hello World!'的信息。

如果有错误，请返回并尝试修复。如果您只看到一个空白页面，请检查运行服务器的控制台窗口是否有错误。

现在是一个很好的时间来承诺你的进步。如果您还没有使用Git，请立即建立存储库。这不是Git教程，所以我不会详细介绍。但使用版本控制应该是一种习惯，即使它只是一个这样的教程项目。

一些编辑器和IDE将自己的文件放入您的项目文件夹。如果是这样，请`.gitignore`在项目根目录中创建一个文件，并排除文件/目录。以下是PHPStorm的示例：

```
.idea/
```

[下一篇 >>](02-composer.md)
