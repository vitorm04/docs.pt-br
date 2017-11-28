---
title: 'Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cbd95c71525a92714ab5758855964e323345b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="5cd58-102">Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="5cd58-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="5cd58-103">Se você inserir informações de um assembly gerenciado de nome forte, você poderá acoplar vagamente tipos em um aplicativo para atingir a independência de versão.</span><span class="sxs-lookup"><span data-stu-id="5cd58-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="5cd58-104">Isto é, seu programa pode ser escrito para usar tipos de várias versões de uma biblioteca gerenciada sem precisar ser recompilado para cada versão.</span><span class="sxs-lookup"><span data-stu-id="5cd58-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="5cd58-105">A incorporação de tipo é frequentemente usada com a interoperabilidade COM, como um aplicativo que usa objetos de automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="5cd58-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="5cd58-106">Inserir informações de tipo permite que o mesmo build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores.</span><span class="sxs-lookup"><span data-stu-id="5cd58-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="5cd58-107">No entanto, você também pode usar a inserção de tipo com uma solução totalmente gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5cd58-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="5cd58-108">As informações de tipo podem ser inseridas de um assembly que tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="5cd58-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="5cd58-109">O assembly expõe pelo menos uma interface pública.</span><span class="sxs-lookup"><span data-stu-id="5cd58-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="5cd58-110">As interfaces inseridas são anotadas com um atributo `ComImport` e um atributo `Guid` (e um GUID único).</span><span class="sxs-lookup"><span data-stu-id="5cd58-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="5cd58-111">O assembly é anotado com o atributo `ImportedFromTypeLib` ou o atributo `PrimaryInteropAssembly` e um atributo `Guid` de nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="5cd58-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="5cd58-112">(Por padrão, os modelos de projeto do Visual C# incluem um atributo `Guid` de nível do assembly.)</span><span class="sxs-lookup"><span data-stu-id="5cd58-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="5cd58-113">Depois de especificar as interfaces públicas que podem ser inseridas, você pode criar classes de tempo de execução que implementam essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="5cd58-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="5cd58-114">Um programa cliente pode, então, inserir as informações de tipo para essas interfaces em tempo de design referenciando o assembly que contém as interfaces públicas e configurando a propriedade `Embed Interop Types` da referência como `True`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="5cd58-115">Isso é equivalente a usar o compilador de linha de comando e fazer referência ao assembly usando a opção do compilador `/link`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="5cd58-116">O programa cliente pode, então, carregar instâncias de seus objetos de tempo de execução de tipo como essas interfaces.</span><span class="sxs-lookup"><span data-stu-id="5cd58-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="5cd58-117">Se você criar uma nova versão do seu assembly de tempo de execução de nome forte, o programa cliente não precisará ser recompilado com o assembly de tempo de execução atualizado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="5cd58-118">Em vez disso, o programa cliente continua a usar qualquer versão do assembly em tempo de execução que está disponível para ele, usando as informações de tipo inseridas para as interfaces públicas.</span><span class="sxs-lookup"><span data-stu-id="5cd58-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="5cd58-119">Como a principal função da inserção de tipo é dar suporte à inserção de informações de tipo dos assemblies de interoperabilidade COM, as limitações a seguir se aplicam ao inserir informações em uma solução totalmente gerenciada:</span><span class="sxs-lookup"><span data-stu-id="5cd58-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="5cd58-120">Somente os atributos específicos à interoperabilidade COM são inseridos, outros atributos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="5cd58-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="5cd58-121">Se um tipo usar parâmetros genéricos e o tipo de parâmetro genérico for um tipo inserido, esse tipo não poderá ser usado em um limite de assembly.</span><span class="sxs-lookup"><span data-stu-id="5cd58-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="5cd58-122">Os exemplos de cruzar um limite de assembly incluem chamar um método de outro assembly ou derivar um tipo de um tipo definido em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="5cd58-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="5cd58-123">Constantes não são inseridas.</span><span class="sxs-lookup"><span data-stu-id="5cd58-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="5cd58-124">A classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> não dá suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="5cd58-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="5cd58-125">Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.</span><span class="sxs-lookup"><span data-stu-id="5cd58-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="5cd58-126">Neste passo a passo, você fará o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5cd58-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="5cd58-127">Criará um assembly de nome forte que tem uma interface pública que contém informações de tipo que podem ser inseridas.</span><span class="sxs-lookup"><span data-stu-id="5cd58-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="5cd58-128">Criará um assembly de tempo de execução de nome forte que implementa a interface pública.</span><span class="sxs-lookup"><span data-stu-id="5cd58-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="5cd58-129">Criará um programa cliente que insere as informações de tipo da interface pública e criará uma instância da classe do assembly de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5cd58-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="5cd58-130">Modificará e recompilará o assembly de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5cd58-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="5cd58-131">Executará o programa cliente para ver se a nova versão do assembly de tempo de execução está sendo usado sem a necessidade de recompilar o programa cliente.</span><span class="sxs-lookup"><span data-stu-id="5cd58-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="5cd58-132">Criando uma interface</span><span class="sxs-lookup"><span data-stu-id="5cd58-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="5cd58-133">Para criar o projeto de interface de equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="5cd58-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="5cd58-134">No Visual Studio, no menu **Arquivo**, escolha **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="5cd58-135">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="5cd58-136">Selecione **Biblioteca de Classes** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="5cd58-137">Na caixa **Nome**, digite `TypeEquivalenceInterface` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="5cd58-138">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="5cd58-139">Em **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo Class1.cs e clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="5cd58-140">Renomeie o arquivo como `ISampleInterface.cs` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="5cd58-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="5cd58-141">Renomear o arquivo também renomeará a classe para `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="5cd58-142">Essa classe representará a interface pública para a classe.</span><span class="sxs-lookup"><span data-stu-id="5cd58-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="5cd58-143">Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="5cd58-144">Clique na guia **Build**. Defina o caminho de saída para um local válido no computador de desenvolvimento, como `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-144">Click the the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="5cd58-145">Esse local também será usado em uma etapa posterior neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="5cd58-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="5cd58-146">Enquanto ainda estiver editando as propriedades do projeto, clique na guia **Assinatura**. Selecione a opção **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="5cd58-147">Na lista **Escolha um arquivo de chave de nome forte**, clique em **<Novo...>**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="5cd58-148">Na caixa **Nome de arquivo de chave**, digite `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="5cd58-149">Desmarque a caixa de seleção **Proteger o arquivo de chaves com senha**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="5cd58-150">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="5cd58-151">Abra o arquivo ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="5cd58-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="5cd58-152">Adicione o seguinte código ao arquivo de classe ISampleInterface para criar a interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="5cd58-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
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
  
7.  <span data-ttu-id="5cd58-153">No menu **Ferramentas**, clique em **Criar GUID**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="5cd58-154">Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="5cd58-155">Clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="5cd58-156">No atributo `Guid`, exclua o GUID de exemplo e cole o GUID que você copiou da caixa de diálogo **Criar GUID**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="5cd58-157">Remova as chaves ({}) do GUID copiado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="5cd58-158">No **Gerenciador de Soluções**, expanda a pasta **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="5cd58-159">Clique duas vezes no arquivo AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="5cd58-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="5cd58-160">Adicione o seguinte atributo ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="5cd58-160">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="5cd58-161">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="5cd58-161">Save the file.</span></span>  
  
10. <span data-ttu-id="5cd58-162">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="5cd58-162">Save the project.</span></span>  
  
11. <span data-ttu-id="5cd58-163">Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="5cd58-164">O arquivo .dll da biblioteca de classes é compilado e salvo no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="5cd58-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="5cd58-165">Criando uma classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5cd58-165">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="5cd58-166">Para criar o projeto de tempo de execução de equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="5cd58-166">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="5cd58-167">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="5cd58-168">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="5cd58-169">Selecione **Biblioteca de Classes** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="5cd58-170">Na caixa **Nome**, digite `TypeEquivalenceRuntime` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="5cd58-171">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-171">The new project is created.</span></span>  
  
3.  <span data-ttu-id="5cd58-172">Em **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo Class1.cs e clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="5cd58-173">Renomeie o arquivo como `SampleClass.cs` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="5cd58-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="5cd58-174">Renomear o arquivo também renomeia a classe para `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="5cd58-175">Essa classe implementará a interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-175">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="5cd58-176">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="5cd58-177">Clique na guia **Build**. Defina o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="5cd58-178">Enquanto ainda estiver editando as propriedades do projeto, clique na guia **Assinatura**. Selecione a opção **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="5cd58-179">Na lista **Escolha um arquivo de chave de nome forte**, clique em **<Novo...>**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-179">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="5cd58-180">Na caixa **Nome de arquivo de chave**, digite `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="5cd58-181">Desmarque a caixa de seleção **Proteger o arquivo de chaves com senha**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="5cd58-182">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-182">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="5cd58-183">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="5cd58-184">Clique na guia **Procurar** e navegue até a pasta do caminho de saída.</span><span class="sxs-lookup"><span data-stu-id="5cd58-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="5cd58-185">Selecione o arquivo TypeEquivalenceInterface.dll e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="5cd58-186">No **Gerenciador de Soluções**, expanda a pasta **Referências**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="5cd58-187">Selecione a referência TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="5cd58-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="5cd58-188">Na janela Propriedades para a referência de TypeEquivalenceInterface, defina a propriedade **Versão Específica** como **False**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="5cd58-189">Adicione o código a seguir ao arquivo de classe SampleClass para criar a classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="5cd58-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
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
    )  
    ```  
  
9. <span data-ttu-id="5cd58-190">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="5cd58-190">Save the project.</span></span>  
  
10. <span data-ttu-id="5cd58-191">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="5cd58-192">O arquivo .dll da biblioteca de classes é compilado e salvo no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="5cd58-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="5cd58-193">Criando um projeto de cliente</span><span class="sxs-lookup"><span data-stu-id="5cd58-193">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="5cd58-194">Para criar o projeto de cliente de equivalência de tipo</span><span class="sxs-lookup"><span data-stu-id="5cd58-194">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="5cd58-195">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="5cd58-196">Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="5cd58-197">Selecione **Aplicativo de Console** no painel **Modelos**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="5cd58-198">Na caixa **Nome**, digite `TypeEquivalenceClient` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="5cd58-199">O novo projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-199">The new project is created.</span></span>  
  
3.  <span data-ttu-id="5cd58-200">Clique com o botão direito do mouse no projeto TypeEquivalenceClient e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="5cd58-201">Clique na guia **Build**. Defina o caminho de saída para o mesmo local usado no projeto TypeEquivalenceInterface, por exemplo, `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="5cd58-202">Clique com o botão direito do mouse no projeto TypeEquivalenceClient e clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="5cd58-203">Clique na guia **Procurar** e navegue até a pasta do caminho de saída.</span><span class="sxs-lookup"><span data-stu-id="5cd58-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="5cd58-204">Selecione o arquivo TypeEquivalenceInterface.dll (não o TypeEquivalenceRuntime.dll) e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="5cd58-205">No **Gerenciador de Soluções**, expanda a pasta **Referências**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="5cd58-206">Selecione a referência TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="5cd58-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="5cd58-207">Na janela Propriedades para a referência de TypeEquivalenceInterface, defina a propriedade **Inserir Tipos de Interoperabilidade** como **True**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="5cd58-208">Adicione o seguinte código ao arquivo Program.cs para criar o programa cliente.</span><span class="sxs-lookup"><span data-stu-id="5cd58-208">Add the following code to the Program.cs file to create the client program.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
    using System.Reflection;  
  
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
  
7.  <span data-ttu-id="5cd58-209">Pressione CTRL+F5 para compilar e executar o programa.</span><span class="sxs-lookup"><span data-stu-id="5cd58-209">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="5cd58-210">Modificando a interface</span><span class="sxs-lookup"><span data-stu-id="5cd58-210">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="5cd58-211">Para modificar a interface</span><span class="sxs-lookup"><span data-stu-id="5cd58-211">To modify the interface</span></span>  
  
1.  <span data-ttu-id="5cd58-212">No Visual Studio, no menu **Arquivo**, aponte para **Abrir** e clique em **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="5cd58-213">Na caixa de diálogo **Abrir Projeto**, clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="5cd58-214">Clique na guia **Aplicativo**. Clique no botão **Informações do Assembly**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="5cd58-215">Altere os valores de **Versão do Assembly** e **Versão do Arquivo** para `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="5cd58-216">Abra o arquivo SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="5cd58-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="5cd58-217">Adicione a linha de código a seguir à interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="5cd58-217">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="5cd58-218">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="5cd58-218">Save the file.</span></span>  
  
4.  <span data-ttu-id="5cd58-219">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="5cd58-219">Save the project.</span></span>  
  
5.  <span data-ttu-id="5cd58-220">Clique com o botão direito do mouse no projeto TypeEquivalenceInterface e clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="5cd58-221">Uma nova versão do arquivo .dll da biblioteca de classes é compilada e salva no caminho de saída de build especificado (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="5cd58-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="5cd58-222">Modificar a classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5cd58-222">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="5cd58-223">Para modificar a classe de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5cd58-223">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="5cd58-224">No Visual Studio, no menu **Arquivo**, aponte para **Abrir** e clique em **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="5cd58-225">Na caixa de diálogo **Abrir Projeto**, clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="5cd58-226">Clique na guia **Aplicativo**. Clique no botão **Informações do Assembly**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="5cd58-227">Altere os valores de **Versão do Assembly** e **Versão do Arquivo** para `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="5cd58-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="5cd58-228">Abra o arquivo SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="5cd58-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="5cd58-229">Adicione as seguintes linhas de código à classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="5cd58-229">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="5cd58-230">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="5cd58-230">Save the file.</span></span>  
  
4.  <span data-ttu-id="5cd58-231">Salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="5cd58-231">Save the project.</span></span>  
  
5.  <span data-ttu-id="5cd58-232">Clique com o botão direito do mouse no projeto TypeEquivalenceRuntime e clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5cd58-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="5cd58-233">Uma versão atualizada do arquivo .dll da biblioteca de classes é compilada e salva no caminho de saída de build especificado anteriormente (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="5cd58-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="5cd58-234">No Explorador de Arquivos, abra a pasta do caminho de saída (por exemplo, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="5cd58-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="5cd58-235">Clique duas vezes em TypeEquivalenceClient.exe para executar o programa.</span><span class="sxs-lookup"><span data-stu-id="5cd58-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="5cd58-236">O programa refletirá a nova versão do assembly TypeEquivalenceRuntime sem ter sido recompilado.</span><span class="sxs-lookup"><span data-stu-id="5cd58-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd58-237">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cd58-237">See Also</span></span>  
 [<span data-ttu-id="5cd58-238">/link (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="5cd58-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="5cd58-239">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5cd58-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5cd58-240">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="5cd58-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="5cd58-241">Assemblies e o Cache de Assembly Global (C#)</span><span class="sxs-lookup"><span data-stu-id="5cd58-241">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
