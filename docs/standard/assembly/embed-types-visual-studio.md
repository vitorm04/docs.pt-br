---
title: 'Passo a passo: Incorporar tipos de montagens gerenciadas no Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338551"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="bb115-102">Passo a passo: Incorporar tipos de montagens gerenciadas no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb115-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="bb115-103">Se você inserir informações de um assembly gerenciado de nome forte, você poderá acoplar vagamente tipos em um aplicativo para atingir a independência de versão.</span><span class="sxs-lookup"><span data-stu-id="bb115-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="bb115-104">Ou seja, seu programa pode ser escrito para usar tipos de qualquer versão de uma biblioteca gerenciada sem ter que ser recompilado para cada nova versão.</span><span class="sxs-lookup"><span data-stu-id="bb115-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="bb115-105">A incorporação de tipo é frequentemente usada com a interoperabilidade COM, como um aplicativo que usa objetos de automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="bb115-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="bb115-106">Inserir informações de tipo permite que o mesmo build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores.</span><span class="sxs-lookup"><span data-stu-id="bb115-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="bb115-107">No entanto, você também pode usar incorporação de tipo com soluções totalmente gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="bb115-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="bb115-108">Depois de especificar as interfaces públicas que podem ser incorporadas, você cria classes de tempo de execução que implementam essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="bb115-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="bb115-109">Um programa cliente pode incorporar as informações do tipo para as interfaces no momento do `Embed Interop Types` projeto, fazendo `True`referência ao conjunto que contém as interfaces públicas e definindo a propriedade da referência a .</span><span class="sxs-lookup"><span data-stu-id="bb115-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="bb115-110">O programa cliente pode então carregar instâncias dos objetos de tempo de execução digitados como essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="bb115-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="bb115-111">Isso equivale a usar o compilador de linha de comando e referenciar o conjunto usando a [opção -link compilador](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="bb115-111">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="bb115-112">Se você criar uma nova versão do seu conjunto de tempo de execução com nome forte, o programa cliente não precisa ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="bb115-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="bb115-113">O programa cliente continua a usar qualquer versão do conjunto de tempo de execução disponível para ele, usando as informações do tipo incorporado para as interfaces públicas.</span><span class="sxs-lookup"><span data-stu-id="bb115-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="bb115-114">Neste passo a passo, você vai:</span><span class="sxs-lookup"><span data-stu-id="bb115-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="bb115-115">Crie um conjunto com nome forte com uma interface pública contendo informações de tipo que podem ser incorporadas.</span><span class="sxs-lookup"><span data-stu-id="bb115-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="bb115-116">Crie um conjunto de tempo de execução com nome forte que implemente a interface pública.</span><span class="sxs-lookup"><span data-stu-id="bb115-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="bb115-117">Criará um programa cliente que insere as informações de tipo da interface pública e criará uma instância da classe do assembly de runtime.</span><span class="sxs-lookup"><span data-stu-id="bb115-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="bb115-118">Modificará e recompilará o assembly de runtime.</span><span class="sxs-lookup"><span data-stu-id="bb115-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="bb115-119">Execute o programa cliente para ver se ele usa a nova versão do conjunto de tempo de execução sem ter que ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="bb115-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="bb115-120">Condições e limitações</span><span class="sxs-lookup"><span data-stu-id="bb115-120">Conditions and limitations</span></span>

<span data-ttu-id="bb115-121">Você pode incorporar informações de tipo a partir de um conjunto nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="bb115-121">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="bb115-122">O assembly expõe pelo menos uma interface pública.</span><span class="sxs-lookup"><span data-stu-id="bb115-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="bb115-123">As interfaces incorporadas são `ComImport` anotadas `Guid` com atributos e atributos com GUIDs exclusivos.</span><span class="sxs-lookup"><span data-stu-id="bb115-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="bb115-124">O assembly é anotado com o atributo `ImportedFromTypeLib` ou o atributo `PrimaryInteropAssembly` e um atributo `Guid` de nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="bb115-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="bb115-125">Os modelos de projeto Visual C# e `Guid` Visual Basic incluem um atributo de nível de montagem por padrão.</span><span class="sxs-lookup"><span data-stu-id="bb115-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="bb115-126">Como a função principal da incorporação de tipos é o suporte a conjuntos de interop COM, as seguintes limitações se aplicam quando você incorpora informações de tipo em uma solução totalmente gerenciada:</span><span class="sxs-lookup"><span data-stu-id="bb115-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="bb115-127">Apenas atributos específicos para com interop são incorporados.</span><span class="sxs-lookup"><span data-stu-id="bb115-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="bb115-128">Outros atributos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="bb115-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="bb115-129">Se um tipo usa parâmetros genéricos, e o tipo do parâmetro genérico é um tipo incorporado, esse tipo não pode ser usado através de um limite de montagem.</span><span class="sxs-lookup"><span data-stu-id="bb115-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="bb115-130">Exemplos de cruzar um limite de montagem incluem chamar um método de outro conjunto ou derivar um tipo de um tipo definido em outro conjunto.</span><span class="sxs-lookup"><span data-stu-id="bb115-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="bb115-131">Constantes não são inseridas.</span><span class="sxs-lookup"><span data-stu-id="bb115-131">Constants are not embedded.</span></span>
- <span data-ttu-id="bb115-132">A classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> não dá suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="bb115-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="bb115-133">Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="bb115-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="bb115-134">Criar uma interface</span><span class="sxs-lookup"><span data-stu-id="bb115-134">Create an interface</span></span>

<span data-ttu-id="bb115-135">O primeiro passo é criar o conjunto de interface de equivalência do tipo.</span><span class="sxs-lookup"><span data-stu-id="bb115-135">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="bb115-136">No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="bb115-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="bb115-137">Na **caixa Criar uma nova** caixa de diálogo de projeto, digite biblioteca de *classes* na caixa **Procurar modelos.**</span><span class="sxs-lookup"><span data-stu-id="bb115-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="bb115-138">Selecione o modelo C# ou Visual Basic **Class Library (.NET Framework)** da lista e selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="bb115-138">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="bb115-139">Na **caixa de diálogo Configurar sua nova** caixa de diálogo de projeto, em nome do **projeto,** *digite TypeEquivalenceInterface*e, em seguida, selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="bb115-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="bb115-140">Quando um novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="bb115-140">The new project is created.</span></span>

1. <span data-ttu-id="bb115-141">No **Solution Explorer,** clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1.vb,* selecione **Renomear**e renomeie o arquivo de *Class1* para *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="bb115-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="bb115-142">Responda **Sim** ao prompt para também `ISampleInterface`renomear a classe para .</span><span class="sxs-lookup"><span data-stu-id="bb115-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="bb115-143">Esta classe representa a interface pública para a classe.</span><span class="sxs-lookup"><span data-stu-id="bb115-143">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="bb115-144">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e, em seguida, selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bb115-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="bb115-145">Selecione **Construir** no painel esquerdo da tela **Propriedades** e definir o **caminho de saída** para um local no computador, como *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="bb115-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="bb115-146">Você usa o mesmo local durante este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="bb115-146">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="bb115-147">Selecione **Assinar** no painel esquerdo da tela **Propriedades** e, em seguida, selecione a caixa De **seleção Assinar.**</span><span class="sxs-lookup"><span data-stu-id="bb115-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="bb115-148">No dropdown para **Escolher um arquivo de chave de nome forte,** selecione **Novo**.</span><span class="sxs-lookup"><span data-stu-id="bb115-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="bb115-149">Na **caixa de diálogo Criar chave de nome** forte, em Nome de **chave,** digite *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="bb115-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="bb115-150">Desmarque o **arquivo proteger minha chave com uma** caixa de seleção de senha e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb115-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="bb115-151">Abra o arquivo de classe *ISampleInterface* no editor de código e `ISampleInterface` substitua seu conteúdo pelo seguinte código para criar a interface:</span><span class="sxs-lookup"><span data-stu-id="bb115-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="bb115-152">No menu **Ferramentas,** selecione **Criar Guia**e, na caixa de diálogo **Criar guid,** selecione **Formato de Registro**.</span><span class="sxs-lookup"><span data-stu-id="bb115-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="bb115-153">Selecione **Copiar**e, em seguida, selecione **Sair**.</span><span class="sxs-lookup"><span data-stu-id="bb115-153">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="bb115-154">No `Guid` atributo do seu código, substitua a guia de amostra pelo GUID copiado e remova os aparelhos (**{ }**).</span><span class="sxs-lookup"><span data-stu-id="bb115-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="bb115-155">No **Solution Explorer,** expanda a pasta **Propriedades** e selecione o *arquivo AssemblyInfo.cs* ou *AssemblyInfo.vb.*</span><span class="sxs-lookup"><span data-stu-id="bb115-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="bb115-156">No editor de código, adicione o seguinte atributo ao arquivo:</span><span class="sxs-lookup"><span data-stu-id="bb115-156">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="bb115-157">Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="bb115-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="bb115-158">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Build**.</span><span class="sxs-lookup"><span data-stu-id="bb115-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="bb115-159">O arquivo DLL da biblioteca de classe é compilado e salvo no caminho de saída de compilação especificado, por exemplo *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="bb115-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="bb115-160">Crie uma classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bb115-160">Create a runtime class</span></span>

<span data-ttu-id="bb115-161">Em seguida, crie a classe de tempo de execução de equivalência de equivalência do tipo.</span><span class="sxs-lookup"><span data-stu-id="bb115-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="bb115-162">No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="bb115-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="bb115-163">Na **caixa Criar uma nova** caixa de diálogo de projeto, digite biblioteca de *classes* na caixa **Procurar modelos.**</span><span class="sxs-lookup"><span data-stu-id="bb115-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="bb115-164">Selecione o modelo C# ou Visual Basic **Class Library (.NET Framework)** da lista e selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="bb115-164">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="bb115-165">Na **caixa de diálogo Configurar sua nova** caixa de diálogo de projeto, em nome do **projeto,** *digite TypeEquivalenceRuntime*e selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="bb115-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="bb115-166">Quando um novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="bb115-166">The new project is created.</span></span>

1. <span data-ttu-id="bb115-167">No **Solution Explorer,** clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1.vb,* selecione **Renomear**e renomeie o arquivo de *Class1* para *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="bb115-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="bb115-168">Responda **Sim** ao prompt para também `SampleClass`renomear a classe para .</span><span class="sxs-lookup"><span data-stu-id="bb115-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="bb115-169">Essa classe implementa a interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="bb115-169">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="bb115-170">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bb115-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="bb115-171">Selecione **Criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="bb115-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="bb115-172">Selecione **Assinar** no painel esquerdo da tela **Propriedades** e, em seguida, selecione a caixa De **seleção Assinar.**</span><span class="sxs-lookup"><span data-stu-id="bb115-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="bb115-173">No dropdown para **Escolher um arquivo de chave de nome forte,** selecione **Novo**.</span><span class="sxs-lookup"><span data-stu-id="bb115-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="bb115-174">Na **caixa de diálogo Criar chave de nome** forte, em Nome de **chave,** digite *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="bb115-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="bb115-175">Desmarque o **arquivo proteger minha chave com uma** caixa de seleção de senha e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb115-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="bb115-176">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Adicionar** > **referência**.</span><span class="sxs-lookup"><span data-stu-id="bb115-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="bb115-177">Na caixa **de diálogo Gerenciador de** referência, **selecione Procurar** e navegar até a pasta de caminho de saída.</span><span class="sxs-lookup"><span data-stu-id="bb115-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="bb115-178">Selecione o *arquivo TypeEquivaleInterface.dll,* selecione **Adicionar**e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb115-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="bb115-179">No **Solution Explorer,** expanda a pasta **Referências** e selecione a referência **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="bb115-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="bb115-180">No painel **Propriedades,** defina **Versão Específica** como **Falsa** se ela ainda não estiver.</span><span class="sxs-lookup"><span data-stu-id="bb115-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="bb115-181">Abra o arquivo de classe *SampleClass* no editor de código e `SampleClass` substitua seu conteúdo pelo seguinte código para criar a classe:</span><span class="sxs-lookup"><span data-stu-id="bb115-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="bb115-182">Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="bb115-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="bb115-183">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Build**.</span><span class="sxs-lookup"><span data-stu-id="bb115-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="bb115-184">O arquivo DLL da biblioteca de classe é compilado e salvo no caminho de saída de compilação especificado.</span><span class="sxs-lookup"><span data-stu-id="bb115-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="bb115-185">Crie um projeto cliente</span><span class="sxs-lookup"><span data-stu-id="bb115-185">Create a client project</span></span>

<span data-ttu-id="bb115-186">Finalmente, crie um programa cliente de equivalência de tipo que faz referência ao conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="bb115-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="bb115-187">No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="bb115-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="bb115-188">Na **caixa Criar uma nova** caixa de diálogo de projeto, digite console na caixa Procurar **modelos.** *console*</span><span class="sxs-lookup"><span data-stu-id="bb115-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="bb115-189">Selecione o modelo C# ou Visual Basic **Console App (.NET Framework)** da lista e selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="bb115-189">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="bb115-190">Na **caixa de diálogo Configurar sua nova** caixa de diálogo de projeto, em nome do **projeto,** *digite TypeEquivalenceClient*e, em seguida, selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="bb115-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="bb115-191">Quando um novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="bb115-191">The new project is created.</span></span>

1. <span data-ttu-id="bb115-192">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bb115-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="bb115-193">Selecione **Criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="bb115-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="bb115-194">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Adicionar** > **referência**.</span><span class="sxs-lookup"><span data-stu-id="bb115-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="bb115-195">Na caixa **de diálogo Gerenciador de** referência, se o arquivo **TypeEquivalenceInterface.dll** já estiver listado, selecione-o.</span><span class="sxs-lookup"><span data-stu-id="bb115-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="bb115-196">Se não, **selecione Procurar**, navegue na pasta de caminho de saída, selecione o arquivo *TypeEquivalenceInterface.dll* (não o *TypeEquivalenceRuntime.dll)* e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="bb115-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="bb115-197">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb115-197">Select **OK**.</span></span>

1. <span data-ttu-id="bb115-198">No **Solution Explorer,** expanda a pasta **Referências** e selecione a referência **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="bb115-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="bb115-199">No painel **Propriedades,** defina **Os Tipos de Interop** de Incorporar como **True**.</span><span class="sxs-lookup"><span data-stu-id="bb115-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="bb115-200">Abra o arquivo *Program.cs* ou *Module1.vb* no editor de código e substitua seu conteúdo pelo seguinte código para criar o programa cliente:</span><span class="sxs-lookup"><span data-stu-id="bb115-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

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

1. <span data-ttu-id="bb115-201">Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="bb115-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="bb115-202">Pressione **Ctrl**+**F5** para construir e executar o programa.</span><span class="sxs-lookup"><span data-stu-id="bb115-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="bb115-203">Observe que a saída do console retorna a versão de montagem **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="bb115-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="bb115-204">Modificar a interface</span><span class="sxs-lookup"><span data-stu-id="bb115-204">Modify the interface</span></span>

<span data-ttu-id="bb115-205">Agora, modifique o conjunto de interface e altere sua versão.</span><span class="sxs-lookup"><span data-stu-id="bb115-205">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="bb115-206">No Visual Studio, selecione > **Projeto/Solução Aberta de** > **Project/Solution** **Arquivo**e abra o projeto **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="bb115-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="bb115-207">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bb115-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="bb115-208">Selecione **''Aplicativo'** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **'Informações de montagem '''**</span><span class="sxs-lookup"><span data-stu-id="bb115-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="bb115-209">Na caixa de diálogo Informações de **montagem,** altere os valores da **versão Assembly** e **file** para *2.0.0.0*e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb115-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="bb115-210">Abra o *arquivo SampleInterface.cs* ou *SampleInterface.vb* e adicione `ISampleInterface` a seguinte linha de código à interface:</span><span class="sxs-lookup"><span data-stu-id="bb115-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="bb115-211">Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="bb115-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="bb115-212">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Build**.</span><span class="sxs-lookup"><span data-stu-id="bb115-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="bb115-213">Uma nova versão do arquivo DLL da biblioteca de classe é compilada e salva no caminho de saída de compilação.</span><span class="sxs-lookup"><span data-stu-id="bb115-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="bb115-214">Modifique a classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bb115-214">Modify the runtime class</span></span>

<span data-ttu-id="bb115-215">Também modifique a classe de tempo de execução e atualize sua versão.</span><span class="sxs-lookup"><span data-stu-id="bb115-215">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="bb115-216">No Visual Studio, selecione > **Projeto/Solução Aberta de** > **Project/Solution** **Arquivo**e abra o projeto **TypeEquivalenceRuntime.**</span><span class="sxs-lookup"><span data-stu-id="bb115-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="bb115-217">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bb115-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="bb115-218">Selecione **''Aplicativo'** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **'Informações de montagem '''**</span><span class="sxs-lookup"><span data-stu-id="bb115-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="bb115-219">Na caixa de diálogo Informações de **montagem,** altere os valores da **versão Assembly** e **file** para *2.0.0.0*e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb115-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="bb115-220">Abra o *arquivo SampleClass.cs* ou *SampleClass.vb* e `SampleClass` adicione o seguinte código à classe:</span><span class="sxs-lookup"><span data-stu-id="bb115-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="bb115-221">Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.</span><span class="sxs-lookup"><span data-stu-id="bb115-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="bb115-222">No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Build**.</span><span class="sxs-lookup"><span data-stu-id="bb115-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="bb115-223">Uma nova versão do arquivo DLL da biblioteca de classe é compilada e salva no caminho de saída de compilação.</span><span class="sxs-lookup"><span data-stu-id="bb115-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="bb115-224">Execute o programa cliente atualizado</span><span class="sxs-lookup"><span data-stu-id="bb115-224">Run the updated client program</span></span>

<span data-ttu-id="bb115-225">Vá para o local da pasta de saída de compilação e execute *TypeEquivalenceClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="bb115-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="bb115-226">Note que a saída do console `TypeEquivalenceRuntime` agora reflete a nova versão do conjunto, *2.0.0.0*, sem que o programa seja recompilado.</span><span class="sxs-lookup"><span data-stu-id="bb115-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb115-227">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb115-227">See also</span></span>

- [<span data-ttu-id="bb115-228">-link (C# Opções de compilador)</span><span class="sxs-lookup"><span data-stu-id="bb115-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="bb115-229">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb115-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="bb115-230">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="bb115-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bb115-231">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb115-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="bb115-232">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="bb115-232">Assemblies in .NET</span></span>](index.md)
