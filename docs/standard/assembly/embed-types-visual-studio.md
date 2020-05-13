---
title: 'Passo a passo: Inserir tipos de assemblies gerenciados no Visual Studio'
description: Este tutorial mostra como inserir tipos de assemblies gerenciados no .NET usando o Visual Studio. Tipos inseridos podem oferecer suporte à independência de versão.
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378980"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="5535d-104">Passo a passo: Inserir tipos de assemblies gerenciados no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5535d-104">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="5535d-105">Se você inserir informações de um assembly gerenciado de nome forte, você poderá acoplar vagamente tipos em um aplicativo para atingir a independência de versão.</span><span class="sxs-lookup"><span data-stu-id="5535d-105">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="5535d-106">Ou seja, seu programa pode ser escrito para usar tipos de qualquer versão de uma biblioteca gerenciada sem precisar ser recompilado para cada nova versão.</span><span class="sxs-lookup"><span data-stu-id="5535d-106">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="5535d-107">A incorporação de tipo é frequentemente usada com a interoperabilidade COM, como um aplicativo que usa objetos de automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="5535d-107">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="5535d-108">Inserir informações de tipo permite que o mesmo build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores.</span><span class="sxs-lookup"><span data-stu-id="5535d-108">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="5535d-109">No entanto, você também pode usar a inserção de tipos com soluções totalmente gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="5535d-109">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="5535d-110">Depois de especificar as interfaces públicas que podem ser incorporadas, você cria classes de tempo de execução que implementam essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="5535d-110">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="5535d-111">Um programa cliente pode inserir as informações de tipo para as interfaces em tempo de design referenciando o assembly que contém as interfaces públicas e definindo a `Embed Interop Types` propriedade da referência como `True` .</span><span class="sxs-lookup"><span data-stu-id="5535d-111">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="5535d-112">O programa cliente pode então carregar instâncias dos objetos de tempo de execução digitados como essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="5535d-112">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="5535d-113">Isso é equivalente a usar o compilador de linha de comando e referenciar o assembly usando a [opção-link do compilador](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5535d-113">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="5535d-114">Se você criar uma nova versão do assembly de tempo de execução de nome forte, o programa cliente não precisará ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="5535d-114">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="5535d-115">O programa cliente continua a usar qualquer versão do assembly de tempo de execução disponível para ele, usando as informações de tipo inserido para as interfaces públicas.</span><span class="sxs-lookup"><span data-stu-id="5535d-115">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="5535d-116">Neste passo a passo, você vai:</span><span class="sxs-lookup"><span data-stu-id="5535d-116">In this walkthrough, you:</span></span>

1. <span data-ttu-id="5535d-117">Crie um assembly de nome forte com uma interface pública contendo informações de tipo que podem ser inseridas.</span><span class="sxs-lookup"><span data-stu-id="5535d-117">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="5535d-118">Crie um assembly de tempo de execução de nome forte que implemente a interface pública.</span><span class="sxs-lookup"><span data-stu-id="5535d-118">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="5535d-119">Criará um programa cliente que insere as informações de tipo da interface pública e criará uma instância da classe do assembly de runtime.</span><span class="sxs-lookup"><span data-stu-id="5535d-119">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="5535d-120">Modificará e recompilará o assembly de runtime.</span><span class="sxs-lookup"><span data-stu-id="5535d-120">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="5535d-121">Execute o programa cliente para ver que ele usa a nova versão do assembly de tempo de execução sem precisar ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="5535d-121">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="5535d-122">Condições e limitações</span><span class="sxs-lookup"><span data-stu-id="5535d-122">Conditions and limitations</span></span>

<span data-ttu-id="5535d-123">Você pode inserir informações de tipo de um assembly sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="5535d-123">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="5535d-124">O assembly expõe pelo menos uma interface pública.</span><span class="sxs-lookup"><span data-stu-id="5535d-124">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="5535d-125">As interfaces inseridas são anotadas com `ComImport` atributos e `Guid` atributos com GUIDs exclusivos.</span><span class="sxs-lookup"><span data-stu-id="5535d-125">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="5535d-126">O assembly é anotado com o atributo `ImportedFromTypeLib` ou o atributo `PrimaryInteropAssembly` e um atributo `Guid` de nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="5535d-126">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="5535d-127">Os modelos de projeto do Visual C# e do Visual Basic incluem um atributo de nível de assembly `Guid` por padrão.</span><span class="sxs-lookup"><span data-stu-id="5535d-127">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="5535d-128">Como a função principal do tipo incorporação é oferecer suporte a assemblies de interoperabilidade COM, as seguintes limitações se aplicam quando você insere informações de tipo em uma solução totalmente gerenciada:</span><span class="sxs-lookup"><span data-stu-id="5535d-128">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="5535d-129">Somente atributos específicos da interoperabilidade COM são inseridos.</span><span class="sxs-lookup"><span data-stu-id="5535d-129">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="5535d-130">Outros atributos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="5535d-130">Other attributes are ignored.</span></span>
- <span data-ttu-id="5535d-131">Se um tipo usa parâmetros genéricos e o tipo do parâmetro genérico é um tipo inserido, esse tipo não pode ser usado em um limite de assembly.</span><span class="sxs-lookup"><span data-stu-id="5535d-131">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="5535d-132">Exemplos de cruzamento de um limite de assembly incluem chamar um método de outro assembly ou derivar um tipo de um tipo definido em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="5535d-132">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="5535d-133">Constantes não são inseridas.</span><span class="sxs-lookup"><span data-stu-id="5535d-133">Constants are not embedded.</span></span>
- <span data-ttu-id="5535d-134">A classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> não dá suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="5535d-134">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="5535d-135">Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="5535d-135">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="5535d-136">Criar uma interface</span><span class="sxs-lookup"><span data-stu-id="5535d-136">Create an interface</span></span>

<span data-ttu-id="5535d-137">A primeira etapa é criar o assembly de interface equivalente do tipo.</span><span class="sxs-lookup"><span data-stu-id="5535d-137">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="5535d-138">No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="5535d-138">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="5535d-139">Na caixa de diálogo **criar um novo projeto** , digite *biblioteca de classes* na caixa **Pesquisar modelos** .</span><span class="sxs-lookup"><span data-stu-id="5535d-139">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="5535d-140">Selecione o modelo de **.NET Framework (biblioteca de classes)** do C# ou do Visual Basic na lista e, em seguida, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-140">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="5535d-141">Na caixa de diálogo **configurar seu novo projeto** , em **nome do projeto**, digite *TypeEquivalenceInterface*e, em seguida, selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-141">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="5535d-142">Quando um novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5535d-142">The new project is created.</span></span>

1. <span data-ttu-id="5535d-143">Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1. vb* , selecione **renomear**e renomeie o arquivo de *Class1* para *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="5535d-143">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="5535d-144">Responda **Sim** à solicitação para também renomear a classe como `ISampleInterface` .</span><span class="sxs-lookup"><span data-stu-id="5535d-144">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="5535d-145">Essa classe representa a interface pública para a classe.</span><span class="sxs-lookup"><span data-stu-id="5535d-145">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="5535d-146">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5535d-146">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="5535d-147">Selecione **criar** no painel esquerdo da tela **Propriedades** e defina o **caminho de saída** para um local em seu computador, como *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="5535d-147">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="5535d-148">Você usa o mesmo local em todo este passo a passos.</span><span class="sxs-lookup"><span data-stu-id="5535d-148">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="5535d-149">Selecione **assinar** no painel esquerdo da tela **Propriedades** e, em seguida, marque a caixa de seleção **assinar o assembly** .</span><span class="sxs-lookup"><span data-stu-id="5535d-149">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="5535d-150">No menu suspenso para **escolher um arquivo de chave de nome forte**, selecione **novo**.</span><span class="sxs-lookup"><span data-stu-id="5535d-150">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="5535d-151">Na caixa de diálogo **criar chave de nome forte** , em **nome do arquivo de chave**, digite *Key. SNK*.</span><span class="sxs-lookup"><span data-stu-id="5535d-151">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="5535d-152">Desmarque a caixa de seleção **proteger meu arquivo de chave com uma senha** e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="5535d-152">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="5535d-153">Abra o arquivo da classe *ISampleInterface* no editor de código e substitua seu conteúdo pelo código a seguir para criar a `ISampleInterface` interface:</span><span class="sxs-lookup"><span data-stu-id="5535d-153">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. <span data-ttu-id="5535d-154">No menu **ferramentas** , selecione **Criar GUID**e, na caixa de diálogo **Criar GUID** , selecione **formato do registro**.</span><span class="sxs-lookup"><span data-stu-id="5535d-154">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="5535d-155">Selecione **copiar**e, em seguida, selecione **sair**.</span><span class="sxs-lookup"><span data-stu-id="5535d-155">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="5535d-156">No `Guid` atributo do seu código, substitua o GUID de exemplo pelo GUID que você copiou e remova as chaves (**{}**).</span><span class="sxs-lookup"><span data-stu-id="5535d-156">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="5535d-157">Em **Gerenciador de soluções**, expanda a pasta **Propriedades** e selecione o arquivo *AssemblyInfo.cs* ou *AssemblyInfo. vb* .</span><span class="sxs-lookup"><span data-stu-id="5535d-157">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="5535d-158">No editor de código, adicione o seguinte atributo ao arquivo:</span><span class="sxs-lookup"><span data-stu-id="5535d-158">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="5535d-159">Selecione **arquivo**  >  **salvar tudo** ou pressione **Ctrl** + **Shift** + **S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="5535d-159">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="5535d-160">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-160">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="5535d-161">O arquivo DLL da biblioteca de classes é compilado e salvo no caminho de saída da compilação especificado, por exemplo, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="5535d-161">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="5535d-162">Criar uma classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5535d-162">Create a runtime class</span></span>

<span data-ttu-id="5535d-163">Em seguida, crie a classe de tempo de execução equivalente do tipo.</span><span class="sxs-lookup"><span data-stu-id="5535d-163">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="5535d-164">No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="5535d-164">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="5535d-165">Na caixa de diálogo **criar um novo projeto** , digite *biblioteca de classes* na caixa **Pesquisar modelos** .</span><span class="sxs-lookup"><span data-stu-id="5535d-165">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="5535d-166">Selecione o modelo de **.NET Framework (biblioteca de classes)** do C# ou do Visual Basic na lista e, em seguida, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-166">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="5535d-167">Na caixa de diálogo **configurar seu novo projeto** , em **nome do projeto**, digite *TypeEquivalenceRuntime*e, em seguida, selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-167">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="5535d-168">Quando um novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5535d-168">The new project is created.</span></span>

1. <span data-ttu-id="5535d-169">Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1. vb* , selecione **renomear**e renomeie o arquivo de *Class1* para *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="5535d-169">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="5535d-170">Responda **Sim** à solicitação para também renomear a classe como `SampleClass` .</span><span class="sxs-lookup"><span data-stu-id="5535d-170">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="5535d-171">Essa classe implementa a interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="5535d-171">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="5535d-172">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5535d-172">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="5535d-173">Selecione **criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="5535d-173">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="5535d-174">Selecione **assinar** no painel esquerdo da tela **Propriedades** e, em seguida, marque a caixa de seleção **assinar o assembly** .</span><span class="sxs-lookup"><span data-stu-id="5535d-174">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="5535d-175">No menu suspenso para **escolher um arquivo de chave de nome forte**, selecione **novo**.</span><span class="sxs-lookup"><span data-stu-id="5535d-175">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="5535d-176">Na caixa de diálogo **criar chave de nome forte** , em **nome do arquivo de chave**, digite *Key. SNK*.</span><span class="sxs-lookup"><span data-stu-id="5535d-176">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="5535d-177">Desmarque a caixa de seleção **proteger meu arquivo de chave com uma senha** e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="5535d-177">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="5535d-178">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Adicionar**  >  **referência**.</span><span class="sxs-lookup"><span data-stu-id="5535d-178">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="5535d-179">Na caixa de diálogo **Gerenciador de referências** , selecione **procurar** e navegue até a pasta caminho de saída.</span><span class="sxs-lookup"><span data-stu-id="5535d-179">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="5535d-180">Selecione o arquivo *TypeEquivalenceInterface. dll* , selecione **Adicionar**e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="5535d-180">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="5535d-181">Em **Gerenciador de soluções**, expanda a pasta **referências** e selecione a referência **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="5535d-181">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="5535d-182">No painel **Propriedades** , defina **versão específica** como **false** se ainda não estiver.</span><span class="sxs-lookup"><span data-stu-id="5535d-182">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="5535d-183">Abra o arquivo da classe *SampleClass* no editor de código e substitua seu conteúdo pelo código a seguir para criar a `SampleClass` classe:</span><span class="sxs-lookup"><span data-stu-id="5535d-183">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

   ```csharp
   using System;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }

           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports TypeEquivalenceInterface

   Public Class SampleClass
       Implements ISampleInterface

       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property

       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```

1. <span data-ttu-id="5535d-184">Selecione **arquivo**  >  **salvar tudo** ou pressione **Ctrl** + **Shift** + **S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="5535d-184">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="5535d-185">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-185">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="5535d-186">O arquivo DLL da biblioteca de classes é compilado e salvo no caminho de saída da compilação especificado.</span><span class="sxs-lookup"><span data-stu-id="5535d-186">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="5535d-187">Criar um projeto de cliente</span><span class="sxs-lookup"><span data-stu-id="5535d-187">Create a client project</span></span>

<span data-ttu-id="5535d-188">Por fim, crie um programa cliente de equivalência de tipo que faça referência ao assembly da interface.</span><span class="sxs-lookup"><span data-stu-id="5535d-188">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="5535d-189">No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="5535d-189">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="5535d-190">Na caixa de diálogo **criar um novo projeto** , digite *console* na caixa **Pesquisar modelos** .</span><span class="sxs-lookup"><span data-stu-id="5535d-190">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="5535d-191">Selecione o modelo de aplicativo de console do C# ou do Visual Basic **(.NET Framework)** na lista e, em seguida, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-191">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="5535d-192">Na caixa de diálogo **configurar seu novo projeto** , em **nome do projeto**, digite *TypeEquivalenceClient*e, em seguida, selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-192">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="5535d-193">Quando um novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5535d-193">The new project is created.</span></span>

1. <span data-ttu-id="5535d-194">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5535d-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="5535d-195">Selecione **criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="5535d-195">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="5535d-196">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Adicionar**  >  **referência**.</span><span class="sxs-lookup"><span data-stu-id="5535d-196">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="5535d-197">Na caixa de diálogo **Gerenciador de referências** , se o arquivo **TypeEquivalenceInterface. dll** já estiver listado, selecione-o.</span><span class="sxs-lookup"><span data-stu-id="5535d-197">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="5535d-198">Caso contrário, selecione **procurar**, navegue até a pasta caminho de saída, selecione o arquivo *TypeEquivalenceInterface. dll* (não o *TypeEquivalenceRuntime. dll*) e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-198">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="5535d-199">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="5535d-199">Select **OK**.</span></span>

1. <span data-ttu-id="5535d-200">Em **Gerenciador de soluções**, expanda a pasta **referências** e selecione a referência **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="5535d-200">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="5535d-201">No painel **Propriedades** , defina **inserir tipos de interoperabilidade** como **true**.</span><span class="sxs-lookup"><span data-stu-id="5535d-201">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="5535d-202">Abra o arquivo *Program.cs* ou *Module1. vb* no editor de código e substitua seu conteúdo pelo código a seguir para criar o programa cliente:</span><span class="sxs-lookup"><span data-stu-id="5535d-202">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

   Module Module1

       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub

   End Module
   ```

1. <span data-ttu-id="5535d-203">Selecione **arquivo**  >  **salvar tudo** ou pressione **Ctrl** + **Shift** + **S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="5535d-203">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="5535d-204">Pressione **Ctrl** + **F5** para compilar e executar o programa.</span><span class="sxs-lookup"><span data-stu-id="5535d-204">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="5535d-205">Observe que a saída do console retorna a versão **1.0.0.0**do assembly.</span><span class="sxs-lookup"><span data-stu-id="5535d-205">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="5535d-206">Modificar a interface</span><span class="sxs-lookup"><span data-stu-id="5535d-206">Modify the interface</span></span>

<span data-ttu-id="5535d-207">Agora, modifique o assembly da interface e altere sua versão.</span><span class="sxs-lookup"><span data-stu-id="5535d-207">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="5535d-208">No Visual Studio, selecione **arquivo**  >  **abrir**  >  **projeto/solução**e abra o projeto **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="5535d-208">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="5535d-209">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5535d-209">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="5535d-210">Selecione **aplicativo** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **informações do assembly**.</span><span class="sxs-lookup"><span data-stu-id="5535d-210">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="5535d-211">Na caixa de diálogo **informações do assembly** , altere a **versão do assembly** e os valores de **versão do arquivo** para *2.0.0.0*e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="5535d-211">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="5535d-212">Abra o arquivo *SampleInterface.cs* ou *SampleInterface. vb* e adicione a seguinte linha de código à `ISampleInterface` interface:</span><span class="sxs-lookup"><span data-stu-id="5535d-212">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="5535d-213">Selecione **arquivo**  >  **salvar tudo** ou pressione **Ctrl** + **Shift** + **S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="5535d-213">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="5535d-214">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-214">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="5535d-215">Uma nova versão do arquivo DLL da biblioteca de classes é compilada e salva no caminho de saída da compilação.</span><span class="sxs-lookup"><span data-stu-id="5535d-215">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="5535d-216">Modificar a classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5535d-216">Modify the runtime class</span></span>

<span data-ttu-id="5535d-217">Além disso, modifique a classe Runtime e atualize sua versão.</span><span class="sxs-lookup"><span data-stu-id="5535d-217">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="5535d-218">No Visual Studio, selecione **arquivo**  >  **abrir**  >  **projeto/solução**e abra o projeto **TypeEquivalenceRuntime** .</span><span class="sxs-lookup"><span data-stu-id="5535d-218">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="5535d-219">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5535d-219">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="5535d-220">Selecione **aplicativo** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **informações do assembly**.</span><span class="sxs-lookup"><span data-stu-id="5535d-220">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="5535d-221">Na caixa de diálogo **informações do assembly** , altere a **versão do assembly** e os valores de **versão do arquivo** para *2.0.0.0*e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="5535d-221">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="5535d-222">Abra o arquivo *SampleClass.cs* ou *SampleClass. vb* e adicione o seguinte código à `SampleClass` classe:</span><span class="sxs-lookup"><span data-stu-id="5535d-222">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. <span data-ttu-id="5535d-223">Selecione **arquivo**  >  **salvar tudo** ou pressione **Ctrl** + **Shift** + **S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="5535d-223">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="5535d-224">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5535d-224">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="5535d-225">Uma nova versão do arquivo DLL da biblioteca de classes é compilada e salva no caminho de saída da compilação.</span><span class="sxs-lookup"><span data-stu-id="5535d-225">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="5535d-226">Executar o programa cliente atualizado</span><span class="sxs-lookup"><span data-stu-id="5535d-226">Run the updated client program</span></span>

<span data-ttu-id="5535d-227">Vá para o local da pasta de saída da compilação e execute *TypeEquivalenceClient. exe*.</span><span class="sxs-lookup"><span data-stu-id="5535d-227">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="5535d-228">Observe que a saída do console agora reflete a nova versão do `TypeEquivalenceRuntime` assembly, *2.0.0.0*, sem que o programa seja recompilado.</span><span class="sxs-lookup"><span data-stu-id="5535d-228">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="5535d-229">Confira também</span><span class="sxs-lookup"><span data-stu-id="5535d-229">See also</span></span>

- [<span data-ttu-id="5535d-230">-link (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="5535d-230">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="5535d-231">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5535d-231">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="5535d-232">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="5535d-232">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5535d-233">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5535d-233">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="5535d-234">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="5535d-234">Assemblies in .NET</span></span>](index.md)
