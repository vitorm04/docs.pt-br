---
title: Como criar exceções definidas pelo usuário com mensagens de exceção localizadas
description: Saiba como criar exceções definidas pelo usuário com mensagens de exceção localizadas
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 5a02c71b16e2c8e5ade5128866af7dc46a03ba4a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160177"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="43103-103">Como criar exceções definidas pelo usuário com mensagens de exceção localizadas</span><span class="sxs-lookup"><span data-stu-id="43103-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="43103-104">Neste artigo, você aprenderá a criar exceções definidas pelo usuário que são herdadas da classe base <xref:System.Exception> com mensagens de exceção localizadas usando assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="43103-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="43103-105">Criar exceções personalizadas</span><span class="sxs-lookup"><span data-stu-id="43103-105">Create custom exceptions</span></span>

<span data-ttu-id="43103-106">O .NET contém muitas exceções diferentes que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="43103-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="43103-107">No entanto, em alguns casos, quando nenhum deles atende às suas necessidades, você pode criar suas próprias exceções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="43103-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="43103-108">Vamos supor que você deseja criar um `StudentNotFoundException` que contenha uma propriedade `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="43103-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="43103-109">Para criar uma exceção personalizada, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="43103-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="43103-110">Crie uma classe serializável que herda de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="43103-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="43103-111">O nome da classe deve terminar em "Exception":</span><span class="sxs-lookup"><span data-stu-id="43103-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. <span data-ttu-id="43103-112">Adicione os construtores padrão:</span><span class="sxs-lookup"><span data-stu-id="43103-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. <span data-ttu-id="43103-113">Defina quaisquer propriedades e construtores adicionais:</span><span class="sxs-lookup"><span data-stu-id="43103-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="43103-114">Criar mensagens de exceção localizadas</span><span class="sxs-lookup"><span data-stu-id="43103-114">Create localized exception messages</span></span>

<span data-ttu-id="43103-115">Você criou uma exceção personalizada e pode jogá-la em qualquer lugar com um código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="43103-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="43103-116">O problema com a linha anterior é que `"The student cannot be found."` é apenas uma cadeia de caracteres constante.</span><span class="sxs-lookup"><span data-stu-id="43103-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="43103-117">Em um aplicativo localizado, você deseja ter mensagens diferentes dependendo da cultura do usuário.</span><span class="sxs-lookup"><span data-stu-id="43103-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="43103-118">Os [assemblies satélite](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) são uma boa maneira de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="43103-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="43103-119">Um assembly satélite é uma. dll que contém recursos para um idioma específico.</span><span class="sxs-lookup"><span data-stu-id="43103-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="43103-120">Quando você solicita recursos específicos em tempo de execução, o CLR encontra esse recurso dependendo da cultura do usuário.</span><span class="sxs-lookup"><span data-stu-id="43103-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="43103-121">Se nenhum assembly satélite for encontrado para essa cultura, os recursos da cultura padrão serão usados.</span><span class="sxs-lookup"><span data-stu-id="43103-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="43103-122">Para criar as mensagens de exceção localizadas:</span><span class="sxs-lookup"><span data-stu-id="43103-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="43103-123">Crie uma nova pasta chamada *recursos* para armazenar os arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="43103-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="43103-124">Adicione um novo arquivo de recurso a ele.</span><span class="sxs-lookup"><span data-stu-id="43103-124">Add a new resource file to it.</span></span> <span data-ttu-id="43103-125">Para fazer isso no Visual Studio, clique com o botão direito do mouse na pasta em **Gerenciador de soluções**e selecione **Adicionar** > **novo item** > **arquivo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="43103-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="43103-126">Nomeie o arquivo *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="43103-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="43103-127">Esse é o arquivo de recursos padrão.</span><span class="sxs-lookup"><span data-stu-id="43103-127">This is the default resources file.</span></span>
1. <span data-ttu-id="43103-128">Adicione um par de nome/valor à mensagem de exceção, como mostra a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="43103-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Adicionar recursos à cultura padrão](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="43103-130">Adicione um novo arquivo de recurso para francês.</span><span class="sxs-lookup"><span data-stu-id="43103-130">Add a new resource file for French.</span></span> <span data-ttu-id="43103-131">Nomeie-o *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="43103-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="43103-132">Adicione um par nome/valor à mensagem de exceção novamente, mas com um valor em francês:</span><span class="sxs-lookup"><span data-stu-id="43103-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![Adicionar recursos à cultura fr-FR](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="43103-134">Depois de compilar o projeto, a pasta de saída da compilação deve conter a pasta *fr-fr* com um arquivo *. dll* , que é o assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="43103-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="43103-135">Você lança a exceção com um código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="43103-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="43103-136">Se o nome do projeto for `TestProject` e o arquivo de recurso *ExceptionMessages. resx* residir na pasta *Resources* do projeto, o nome totalmente qualificado do arquivo de recurso será `TestProject.Resources.ExceptionMessages`.</span><span class="sxs-lookup"><span data-stu-id="43103-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="43103-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="43103-137">See also</span></span>

- [<span data-ttu-id="43103-138">Como criar exceções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="43103-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="43103-139">Criando assemblies satélite para aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="43103-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="43103-140">base (C# referência)</span><span class="sxs-lookup"><span data-stu-id="43103-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="43103-141">isso (C# referência)</span><span class="sxs-lookup"><span data-stu-id="43103-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
