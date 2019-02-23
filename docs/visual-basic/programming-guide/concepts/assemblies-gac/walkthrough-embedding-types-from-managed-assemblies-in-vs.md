---
title: 'Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: f14a3e41c00ae307086a6d3745d4ec76b772721c
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747538"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="616f5-102">Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="616f5-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="616f5-103">Se você inserir informações de um assembly gerenciado de nome forte, você poderá acoplar vagamente tipos em um aplicativo para atingir a independência de versão.</span><span class="sxs-lookup"><span data-stu-id="616f5-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="616f5-104">Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca gerenciada sem precisar ser recompilado para cada versão.</span><span class="sxs-lookup"><span data-stu-id="616f5-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="616f5-105">A incorporação de tipo é frequentemente usada com a interoperabilidade COM, como um aplicativo que usa objetos de automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="616f5-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="616f5-106">Inserir informações de tipo permite que o mesmo build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores.</span><span class="sxs-lookup"><span data-stu-id="616f5-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="616f5-107">No entanto, você também pode usar a inserção de tipo com uma solução totalmente gerenciada.</span><span class="sxs-lookup"><span data-stu-id="616f5-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="616f5-108">As informações de tipo podem ser inseridas de um assembly que tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="616f5-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="616f5-109">O assembly expõe pelo menos uma interface pública.</span><span class="sxs-lookup"><span data-stu-id="616f5-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="616f5-110">As interfaces inseridas são anotadas com um atributo `ComImport` e um atributo `Guid` (e um GUID único).</span><span class="sxs-lookup"><span data-stu-id="616f5-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="616f5-111">O assembly é anotado com o atributo `ImportedFromTypeLib` ou o atributo `PrimaryInteropAssembly` e um atributo `Guid` de nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="616f5-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="616f5-112">(Por padrão, os modelos de projeto do Visual Basic incluem um nível de conjunto `Guid` atributo.)</span><span class="sxs-lookup"><span data-stu-id="616f5-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="616f5-113">Depois de especificar as interfaces públicas que podem ser inseridas, você pode criar classes de tempo de execução que implementam essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="616f5-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="616f5-114">Um programa cliente pode, então, inserir as informações de tipo para essas interfaces em tempo de design referenciando o assembly que contém as interfaces públicas e configurando a propriedade `Embed Interop Types` da referência como `True`.</span><span class="sxs-lookup"><span data-stu-id="616f5-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="616f5-115">Isso é equivalente a usar o compilador de linha de comando e fazer referência ao assembly usando a opção do compilador `/link`.</span><span class="sxs-lookup"><span data-stu-id="616f5-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="616f5-116">O programa cliente pode, então, carregar instâncias de seus objetos de tempo de execução de tipo como essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="616f5-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="616f5-117">Se você criar uma nova versão do seu assembly de tempo de execução de nome forte, o programa cliente não precisará ser recompilado com o assembly de tempo de execução atualizado.</span><span class="sxs-lookup"><span data-stu-id="616f5-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="616f5-118">Em vez disso, o programa cliente continua a usar qualquer versão do assembly em tempo de execução que está disponível para ele, usando as informações de tipo inseridas para as interfaces públicas.</span><span class="sxs-lookup"><span data-stu-id="616f5-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="616f5-119">Como a principal função da inserção de tipo é dar suporte à inserção de informações de tipo dos assemblies de interoperabilidade COM, as limitações a seguir se aplicam ao inserir informações em uma solução totalmente gerenciada:</span><span class="sxs-lookup"><span data-stu-id="616f5-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="616f5-120">Somente os atributos específicos à interoperabilidade COM são inseridos, outros atributos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="616f5-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="616f5-121">Se um tipo usar parâmetros genéricos e o tipo de parâmetro genérico for um tipo inserido, esse tipo não poderá ser usado em um limite de assembly.</span><span class="sxs-lookup"><span data-stu-id="616f5-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="616f5-122">Os exemplos de cruzar um limite de assembly incluem chamar um método de outro assembly ou derivar um tipo de um tipo definido em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="616f5-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="616f5-123">Constantes não são inseridas.</span><span class="sxs-lookup"><span data-stu-id="616f5-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="616f5-124">A classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> não dá suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="616f5-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="616f5-125">Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="616f5-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="616f5-126">Neste passo a passo, você fará o seguinte:</span><span class="sxs-lookup"><span data-stu-id="616f5-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="616f5-127">Criará um assembly de nome forte que tem uma interface pública que contém informações de tipo que podem ser inseridas.</span><span class="sxs-lookup"><span data-stu-id="616f5-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="616f5-128">Criará um assembly de tempo de execução de nome forte que implementa a interface pública.</span><span class="sxs-lookup"><span data-stu-id="616f5-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="616f5-129">Criará um programa cliente que insere as informações de tipo da interface pública e criará uma instância da classe do assembly de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="616f5-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="616f5-130">Modificará e recompilará o assembly de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="616f5-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="616f5-131">Executará o programa cliente para ver se a nova versão do assembly de tempo de execução está sendo usado sem a necessidade de recompilar o programa cliente.</span><span class="sxs-lookup"><span data-stu-id="616f5-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="616f5-132">Criando uma interface</span><span class="sxs-lookup"><span data-stu-id="616f5-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="616f5-133">Para criar o projeto de interface de equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="616f5-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="616f5-134">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="616f5-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="616f5-135">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="616f5-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="616f5-136">Selecione **Biblioteca de Classes** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="616f5-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="616f5-137">Na caixa **Nome**, digite `TypeEquivalenceInterface` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="616f5-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="616f5-138">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="616f5-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="616f5-139">Na **Gerenciador de soluções**, o arquivo Class1.vb com o botão direito e clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="616f5-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="616f5-140">Renomeie o arquivo como `ISampleInterface.vb` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="616f5-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="616f5-141">Renomear o arquivo também renomeará a classe para `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="616f5-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="616f5-142">Essa classe representará a interface pública para a classe.</span><span class="sxs-lookup"><span data-stu-id="616f5-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="616f5-143">Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="616f5-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="616f5-144">Clique na guia **Compilar**. Defina o caminho de saída para um local válido no computador de desenvolvimento, como `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="616f5-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="616f5-145">Esse local também será usado em uma etapa posterior neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="616f5-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="616f5-146">Enquanto ainda estiver editando as propriedades do projeto, clique na guia **Assinatura**. Selecione a opção **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="616f5-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="616f5-147">Na lista **Escolha um arquivo de chave de nome forte**, clique em **<Novo...>**.</span><span class="sxs-lookup"><span data-stu-id="616f5-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="616f5-148">Na caixa **Nome de arquivo de chave**, digite `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="616f5-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="616f5-149">Desmarque a caixa de seleção **Proteger o arquivo de chaves com senha**.</span><span class="sxs-lookup"><span data-stu-id="616f5-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="616f5-150">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="616f5-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="616f5-151">Abra o arquivo ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="616f5-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="616f5-152">Adicione o seguinte código ao arquivo de classe ISampleInterface para criar a interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="616f5-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  <span data-ttu-id="616f5-153">No menu **Ferramentas**, clique em **Criar GUID**.</span><span class="sxs-lookup"><span data-stu-id="616f5-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="616f5-154">Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="616f5-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="616f5-155">Clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="616f5-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="616f5-156">No atributo `Guid`, exclua o GUID de exemplo e cole o GUID que você copiou da caixa de diálogo **Criar GUID**.</span><span class="sxs-lookup"><span data-stu-id="616f5-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="616f5-157">Remova as chaves ({}) do GUID copiado.</span><span class="sxs-lookup"><span data-stu-id="616f5-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="616f5-158">No menu **Projeto**, clique em **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="616f5-158">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="616f5-159">Na **Gerenciador de soluções**, expanda o **My Project** pasta.</span><span class="sxs-lookup"><span data-stu-id="616f5-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="616f5-160">Clique duas vezes o AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="616f5-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="616f5-161">Adicione o seguinte atributo ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="616f5-161">Add the following attribute to the file.</span></span>  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     <span data-ttu-id="616f5-162">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="616f5-162">Save the file.</span></span>  
  
11. <span data-ttu-id="616f5-163">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="616f5-163">Save the project.</span></span>  
  
12. <span data-ttu-id="616f5-164">Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="616f5-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="616f5-165">O arquivo .dll da biblioteca de classes é compilado e salvo no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="616f5-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="616f5-166">Criando uma classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="616f5-166">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="616f5-167">Para criar o projeto de tempo de execução de equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="616f5-167">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="616f5-168">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="616f5-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="616f5-169">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="616f5-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="616f5-170">Selecione **Biblioteca de Classes** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="616f5-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="616f5-171">Na caixa **Nome**, digite `TypeEquivalenceRuntime` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="616f5-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="616f5-172">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="616f5-172">The new project is created.</span></span>  
  
3.  <span data-ttu-id="616f5-173">Na **Gerenciador de soluções**, o arquivo Class1.vb com o botão direito e clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="616f5-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="616f5-174">Renomeie o arquivo como `SampleClass.vb` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="616f5-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="616f5-175">Renomear o arquivo também renomeia a classe para `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="616f5-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="616f5-176">Essa classe implementará a interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="616f5-176">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="616f5-177">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="616f5-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="616f5-178">Clique na guia **Compilar**. Defina o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="616f5-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="616f5-179">Enquanto ainda estiver editando as propriedades do projeto, clique na guia **Assinatura**. Selecione a opção **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="616f5-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="616f5-180">Na lista **Escolha um arquivo de chave de nome forte**, clique em **<Novo...>**.</span><span class="sxs-lookup"><span data-stu-id="616f5-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="616f5-181">Na caixa **Nome de arquivo de chave**, digite `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="616f5-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="616f5-182">Desmarque a caixa de seleção **Proteger o arquivo de chaves com senha**.</span><span class="sxs-lookup"><span data-stu-id="616f5-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="616f5-183">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="616f5-183">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="616f5-184">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="616f5-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="616f5-185">Clique na guia **Procurar** e navegue até a pasta do caminho de saída.</span><span class="sxs-lookup"><span data-stu-id="616f5-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="616f5-186">Selecione o arquivo TypeEquivalenceInterface.dll e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="616f5-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="616f5-187">No menu **Projeto**, clique em **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="616f5-187">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="616f5-188">No **Gerenciador de Soluções**, expanda a pasta **Referências**.</span><span class="sxs-lookup"><span data-stu-id="616f5-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="616f5-189">Selecione a referência TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="616f5-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="616f5-190">Na janela Propriedades para a referência de TypeEquivalenceInterface, defina a propriedade **Versão Específica** como **False**.</span><span class="sxs-lookup"><span data-stu-id="616f5-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="616f5-191">Adicione o código a seguir ao arquivo de classe SampleClass para criar a classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="616f5-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
  
10. <span data-ttu-id="616f5-192">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="616f5-192">Save the project.</span></span>  
  
11. <span data-ttu-id="616f5-193">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="616f5-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="616f5-194">O arquivo .dll da biblioteca de classes é compilado e salvo no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="616f5-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="616f5-195">Criando um projeto de cliente</span><span class="sxs-lookup"><span data-stu-id="616f5-195">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="616f5-196">Para criar o projeto de cliente de equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="616f5-196">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="616f5-197">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="616f5-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="616f5-198">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="616f5-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="616f5-199">Selecione **Aplicativo de Console** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="616f5-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="616f5-200">Na caixa **Nome**, digite `TypeEquivalenceClient` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="616f5-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="616f5-201">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="616f5-201">The new project is created.</span></span>  
  
3.  <span data-ttu-id="616f5-202">Clique com o botão direito do mouse no projeto TypeEquivalenceClient e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="616f5-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="616f5-203">Clique na guia **Compilar**. Defina o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="616f5-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="616f5-204">Clique com o botão direito do mouse no projeto TypeEquivalenceClient e clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="616f5-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="616f5-205">Clique na guia **Procurar** e navegue até a pasta do caminho de saída.</span><span class="sxs-lookup"><span data-stu-id="616f5-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="616f5-206">Selecione o arquivo TypeEquivalenceInterface.dll (não o TypeEquivalenceRuntime.dll) e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="616f5-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="616f5-207">No menu **Projeto**, clique em **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="616f5-207">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="616f5-208">No **Gerenciador de Soluções**, expanda a pasta **Referências**.</span><span class="sxs-lookup"><span data-stu-id="616f5-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="616f5-209">Selecione a referência TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="616f5-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="616f5-210">Na janela Propriedades para a referência de TypeEquivalenceInterface, defina a propriedade **Inserir Tipos de Interoperabilidade** como **True**.</span><span class="sxs-lookup"><span data-stu-id="616f5-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="616f5-211">Adicione o seguinte código ao arquivo Module1.vb para criar o programa cliente.</span><span class="sxs-lookup"><span data-stu-id="616f5-211">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
    ```vb  
    Imports TypeEquivalenceInterface  
    Imports System.Reflection  
  
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
  
8.  <span data-ttu-id="616f5-212">Pressione CTRL+F5 para compilar e executar o programa.</span><span class="sxs-lookup"><span data-stu-id="616f5-212">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="616f5-213">Modificando a interface</span><span class="sxs-lookup"><span data-stu-id="616f5-213">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="616f5-214">Para modificar a interface</span><span class="sxs-lookup"><span data-stu-id="616f5-214">To modify the interface</span></span>  
  
1.  <span data-ttu-id="616f5-215">No Visual Studio, no menu **Arquivo**, aponte para **Abrir** e clique em **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="616f5-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="616f5-216">Na caixa de diálogo **Abrir Projeto**, clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="616f5-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="616f5-217">Clique na guia **Aplicativo**. Clique no botão **Informações do Assembly**.</span><span class="sxs-lookup"><span data-stu-id="616f5-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="616f5-218">Altere os valores de **Versão do Assembly** e **Versão do Arquivo** para `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="616f5-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="616f5-219">Abra o arquivo ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="616f5-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="616f5-220">Adicione a linha de código a seguir à interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="616f5-220">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     <span data-ttu-id="616f5-221">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="616f5-221">Save the file.</span></span>  
  
4.  <span data-ttu-id="616f5-222">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="616f5-222">Save the project.</span></span>  
  
5.  <span data-ttu-id="616f5-223">Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="616f5-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="616f5-224">Uma nova versão do arquivo .dll da biblioteca de classes é compilada e salva no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="616f5-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="616f5-225">Modificar a classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="616f5-225">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="616f5-226">Para modificar a classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="616f5-226">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="616f5-227">No Visual Studio, no menu **Arquivo**, aponte para **Abrir** e clique em **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="616f5-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="616f5-228">Na caixa de diálogo **Abrir Projeto**, clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="616f5-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="616f5-229">Clique na guia **Aplicativo**. Clique no botão **Informações do Assembly**.</span><span class="sxs-lookup"><span data-stu-id="616f5-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="616f5-230">Altere os valores de **Versão do Assembly** e **Versão do Arquivo** para `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="616f5-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="616f5-231">Abra o SampleClass.vbfile.</span><span class="sxs-lookup"><span data-stu-id="616f5-231">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="616f5-232">Adicione as seguintes linhas de código à classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="616f5-232">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="616f5-233">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="616f5-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="616f5-234">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="616f5-234">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="616f5-235">Uma versão atualizada do arquivo .dll da biblioteca de classes é compilada e salva no caminho de saída de build especificado anteriormente (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="616f5-235">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="616f5-236">No Explorador de Arquivos, abra a pasta do caminho de saída (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="616f5-236">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="616f5-237">Clique duas vezes em TypeEquivalenceClient.exe para executar o programa.</span><span class="sxs-lookup"><span data-stu-id="616f5-237">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="616f5-238">O programa refletirá a nova versão do assembly TypeEquivalenceRuntime sem ter sido recompilado.</span><span class="sxs-lookup"><span data-stu-id="616f5-238">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="616f5-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="616f5-239">See also</span></span>
- [<span data-ttu-id="616f5-240">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="616f5-240">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="616f5-241">Conceitos de Programação</span><span class="sxs-lookup"><span data-stu-id="616f5-241">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="616f5-242">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="616f5-242">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="616f5-243">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="616f5-243">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
