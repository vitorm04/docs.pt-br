---
title: 'Como: criar exceções definidas pelo usuário com mensagens de exceção localizadas'
description: Saiba como criar exceções definidas pelo usuário com mensagens de exceção localizadas
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: 1e5ef5658e4cb71d0689a1786494eaec57d4e7fb
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332987"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="37d77-103">Como: criar exceções definidas pelo usuário com mensagens de exceção localizadas</span><span class="sxs-lookup"><span data-stu-id="37d77-103">How to: create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="37d77-104">Neste artigo, você aprenderá a criar exceções definidas pelo usuário que são herdadas da classe base <xref:System.Exception> com mensagens de exceção localizadas usando assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="37d77-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="37d77-105">Criar exceções personalizadas</span><span class="sxs-lookup"><span data-stu-id="37d77-105">Create custom exceptions</span></span>

<span data-ttu-id="37d77-106">O .NET contém muitas exceções diferentes que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="37d77-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="37d77-107">No entanto, em alguns casos, quando nenhum deles atende às suas necessidades, você pode criar suas próprias exceções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="37d77-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="37d77-108">Vamos supor que você deseja criar um `StudentNotFoundException` que contenha uma propriedade `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="37d77-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="37d77-109">Para criar uma exceção personalizada, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="37d77-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="37d77-110">Crie uma classe serializável que herde de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="37d77-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="37d77-111">O nome da classe deve terminar em "Exception":</span><span class="sxs-lookup"><span data-stu-id="37d77-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. <span data-ttu-id="37d77-112">Adicione os construtores padrão:</span><span class="sxs-lookup"><span data-stu-id="37d77-112">Add the default constructors:</span></span>

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

1. <span data-ttu-id="37d77-113">Defina quaisquer propriedades e construtores adicionais:</span><span class="sxs-lookup"><span data-stu-id="37d77-113">Define any additional properties and constructors:</span></span>

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

## <a name="create-localized-exception-messages"></a><span data-ttu-id="37d77-114">Criar mensagens de exceção localizadas</span><span class="sxs-lookup"><span data-stu-id="37d77-114">Create localized exception messages</span></span>

<span data-ttu-id="37d77-115">Você criou uma exceção personalizada e pode jogá-la em qualquer lugar com um código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="37d77-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

<span data-ttu-id="37d77-116">O problema com a linha anterior é que "o aluno não pode ser encontrado".</span><span class="sxs-lookup"><span data-stu-id="37d77-116">The problem with the previous line is that "The student cannot be found."</span></span> <span data-ttu-id="37d77-117">é apenas uma cadeia de caracteres constante.</span><span class="sxs-lookup"><span data-stu-id="37d77-117">is just a constant string.</span></span> <span data-ttu-id="37d77-118">Em um aplicativo localizado, você deseja ter mensagens diferentes dependendo da cultura do usuário.</span><span class="sxs-lookup"><span data-stu-id="37d77-118">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="37d77-119">Os [assemblies satélite](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) são uma boa maneira de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="37d77-119">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="37d77-120">Um assembly satélite é uma. dll que contém recursos para um idioma específico.</span><span class="sxs-lookup"><span data-stu-id="37d77-120">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="37d77-121">Quando você solicita recursos específicos em tempo de execução, o CLR encontra esse recurso dependendo da cultura do usuário.</span><span class="sxs-lookup"><span data-stu-id="37d77-121">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="37d77-122">Se nenhum assembly satélite for encontrado para essa cultura, os recursos da cultura padrão serão usados.</span><span class="sxs-lookup"><span data-stu-id="37d77-122">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="37d77-123">Para criar as mensagens de exceção localizadas:</span><span class="sxs-lookup"><span data-stu-id="37d77-123">To create the localized exception messages:</span></span>

1. <span data-ttu-id="37d77-124">Crie uma nova pasta chamada *recursos* para armazenar os arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="37d77-124">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="37d77-125">Adicione um novo arquivo de recurso a ele.</span><span class="sxs-lookup"><span data-stu-id="37d77-125">Add a new resource file to it.</span></span> <span data-ttu-id="37d77-126">Para fazer isso no Visual Studio, clique com o botão direito do mouse na pasta em **Gerenciador de soluções**e selecione **Adicionar** -> **novo item** -> **arquivo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="37d77-126">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** -> **New Item** -> **Resources File**.</span></span> <span data-ttu-id="37d77-127">Nomeie o arquivo *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="37d77-127">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="37d77-128">Esse é o arquivo de recursos padrão.</span><span class="sxs-lookup"><span data-stu-id="37d77-128">This is the default resources file.</span></span>
1. <span data-ttu-id="37d77-129">Adicione um par de nome/valor à mensagem de exceção, como mostra a imagem a seguir: recursos de @no__t 0Add para a cultura padrão @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="37d77-129">Add a name/value pair for your exception message, like the following image shows: ![Add resources to the default culture](media/add-resources-to-default-culture.jpg)</span></span>
1. <span data-ttu-id="37d77-130">Adicione um novo arquivo de recurso para francês.</span><span class="sxs-lookup"><span data-stu-id="37d77-130">Add a new resource file for French.</span></span> <span data-ttu-id="37d77-131">Nomeie-o *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="37d77-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="37d77-132">Adicione um par nome/valor à mensagem de exceção novamente, mas com um valor em francês: recursos de @no__t 0Add para a cultura fr-FR @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="37d77-132">Add a name/value pair for the exception message again, but with a French value: ![Add resources to the fr-FR culture](media/add-resources-to-fr-culture.jpg)</span></span>
1. <span data-ttu-id="37d77-133">Depois de compilar o projeto, a pasta de saída da compilação deve conter a pasta *fr-fr* com um arquivo *. dll* , que é o assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="37d77-133">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="37d77-134">Você lança a exceção com um código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="37d77-134">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > <span data-ttu-id="37d77-135">Se o nome do projeto for `TestProject` e o arquivo de recurso *ExceptionMessages. resx* residir na pasta *Resources* do projeto, o nome totalmente qualificado do arquivo de recurso será `TestProject.Resources.ExceptionMessages`.</span><span class="sxs-lookup"><span data-stu-id="37d77-135">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="37d77-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37d77-136">See also</span></span>

- [<span data-ttu-id="37d77-137">Como criar exceções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="37d77-137">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="37d77-138">Criando assemblies satélite para aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="37d77-138">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="37d77-139">base (C# referência)</span><span class="sxs-lookup"><span data-stu-id="37d77-139">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="37d77-140">isso (C# referência)</span><span class="sxs-lookup"><span data-stu-id="37d77-140">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
