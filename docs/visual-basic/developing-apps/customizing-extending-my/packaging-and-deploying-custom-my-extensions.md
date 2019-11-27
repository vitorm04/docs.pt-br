---
title: Empacotando e implantando minhas extensões personalizadas
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330256"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="27c9b-102">Empacotar e implantar minhas extensões personalizadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27c9b-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="27c9b-103">Visual Basic fornece uma maneira fácil de implantar suas extensões de namespace de `My` personalizadas usando modelos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27c9b-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="27c9b-104">Se você estiver criando um modelo de projeto para o qual suas extensões de `My` são parte integrante do novo tipo de projeto, você pode apenas incluir o código de extensão de `My` personalizado com o projeto ao exportar o modelo.</span><span class="sxs-lookup"><span data-stu-id="27c9b-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="27c9b-105">Para obter mais informações sobre como exportar modelos de projeto, consulte [como: criar modelos de projeto](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="27c9b-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="27c9b-106">Se a extensão de `My` personalizada estiver em um único arquivo de código, você poderá exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="27c9b-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="27c9b-107">Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e comportamento para sua extensão de `My` personalizada em um projeto Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="27c9b-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="27c9b-108">Esses recursos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="27c9b-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="27c9b-109">Permitir que os usuários gerenciem sua extensão de `My` personalizada na página **minhas extensões** do designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="27c9b-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="27c9b-110">Adicionar automaticamente sua extensão de `My` personalizada quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="27c9b-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="27c9b-111">Ocultando o modelo de item de extensão `My` na caixa de diálogo **Adicionar item** para que ele não seja incluído na lista de itens de projeto.</span><span class="sxs-lookup"><span data-stu-id="27c9b-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="27c9b-112">Este tópico discute como empacotar uma extensão de `My` personalizada como um modelo de item oculto que pode ser gerenciado na página **minhas extensões** do designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="27c9b-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="27c9b-113">A extensão de `My` personalizada também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="27c9b-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="27c9b-114">Criar uma extensão de namespace My</span><span class="sxs-lookup"><span data-stu-id="27c9b-114">Create a My namespace extension</span></span>

<span data-ttu-id="27c9b-115">A primeira etapa na criação de um pacote de implantação para uma extensão de `My` personalizada é criar a extensão como um único arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="27c9b-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="27c9b-116">Para obter detalhes e orientações sobre como criar uma extensão de `My` personalizada, consulte [estendendo o namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="27c9b-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="27c9b-117">Exportar uma extensão de namespace My como um modelo de item</span><span class="sxs-lookup"><span data-stu-id="27c9b-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="27c9b-118">Depois de ter um arquivo de código que inclui sua extensão de namespace `My`, você pode exportar o arquivo de código como um modelo de item do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27c9b-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="27c9b-119">Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [como: criar modelos de item](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="27c9b-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="27c9b-120">Se sua extensão de namespace de `My` tiver uma dependência em um assembly específico, você poderá personalizar seu modelo de item para instalar automaticamente sua extensão de namespace de `My` quando uma referência a esse assembly for adicionada.</span><span class="sxs-lookup"><span data-stu-id="27c9b-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="27c9b-121">Como resultado, você desejará excluir essa referência de assembly ao exportar o arquivo de código como um modelo de item do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27c9b-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="27c9b-122">Personalizar o modelo de item</span><span class="sxs-lookup"><span data-stu-id="27c9b-122">Customize the item template</span></span>

<span data-ttu-id="27c9b-123">Você pode habilitar o modelo de item a ser gerenciado na página **minhas extensões** do designer de projeto Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="27c9b-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="27c9b-124">Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um assembly especificado for adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="27c9b-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="27c9b-125">Para habilitar essas personalizações, você adicionará um novo arquivo, chamado de arquivo CustomData, ao seu modelo e, em seguida, adicionará um novo elemento ao XML em seu arquivo. vstemplate.</span><span class="sxs-lookup"><span data-stu-id="27c9b-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="27c9b-126">Adicionar o arquivo CustomData</span><span class="sxs-lookup"><span data-stu-id="27c9b-126">Add the CustomData file</span></span>

<span data-ttu-id="27c9b-127">O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo de. CustomData (o nome do arquivo pode ser definido como qualquer valor significativo para seu modelo) e que contém XML.</span><span class="sxs-lookup"><span data-stu-id="27c9b-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="27c9b-128">O XML no arquivo CustomData instrui Visual Basic a incluir sua extensão de `My` quando os usuários usam a página **minhas extensões** do designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="27c9b-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="27c9b-129">Opcionalmente, você pode adicionar o atributo <`AssemblyFullName>` ao XML do arquivo CustomData.</span><span class="sxs-lookup"><span data-stu-id="27c9b-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="27c9b-130">Isso instrui Visual Basic a instalar automaticamente sua extensão de `My` personalizada quando uma referência a um determinado assembly for adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="27c9b-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="27c9b-131">Você pode usar qualquer editor de texto ou editor de XML para criar o arquivo CustomData e, em seguida, adicioná-lo à pasta compactada do modelo de item (arquivo. zip).</span><span class="sxs-lookup"><span data-stu-id="27c9b-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="27c9b-132">Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que adicionará o item de modelo à pasta minhas extensões de um projeto Visual Basic quando uma referência ao assembly Microsoft. VisualBasic. PowerPacks. vs. dll for adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="27c9b-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="27c9b-133">O arquivo CustomData contém um elemento <`VBMyExtensionTemplate>` que tem atributos, conforme listado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="27c9b-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="27c9b-134">Atributo</span><span class="sxs-lookup"><span data-stu-id="27c9b-134">Attribute</span></span>|<span data-ttu-id="27c9b-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="27c9b-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="27c9b-136">Necessária.</span><span class="sxs-lookup"><span data-stu-id="27c9b-136">Required.</span></span> <span data-ttu-id="27c9b-137">Um identificador exclusivo para a extensão.</span><span class="sxs-lookup"><span data-stu-id="27c9b-137">A unique identifier for the extension.</span></span> <span data-ttu-id="27c9b-138">Se a extensão que tem essa ID já tiver sido adicionada ao projeto, o usuário não será solicitado a adicioná-la novamente.</span><span class="sxs-lookup"><span data-stu-id="27c9b-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="27c9b-139">Necessária.</span><span class="sxs-lookup"><span data-stu-id="27c9b-139">Required.</span></span> <span data-ttu-id="27c9b-140">Um número de versão para o modelo de item.</span><span class="sxs-lookup"><span data-stu-id="27c9b-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="27c9b-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="27c9b-141">Optional.</span></span> <span data-ttu-id="27c9b-142">Um nome de assembly.</span><span class="sxs-lookup"><span data-stu-id="27c9b-142">An assembly name.</span></span> <span data-ttu-id="27c9b-143">Quando uma referência a esse assembly é adicionada ao projeto, o usuário será solicitado a adicionar a extensão de `My` a partir deste modelo de item.</span><span class="sxs-lookup"><span data-stu-id="27c9b-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="27c9b-144">Adicione o elemento \<CustomDataSignature > ao arquivo. vstemplate</span><span class="sxs-lookup"><span data-stu-id="27c9b-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="27c9b-145">Para identificar o modelo de item do Visual Studio como uma extensão de namespace `My`, você também deve modificar o arquivo. vstemplate para seu modelo de item.</span><span class="sxs-lookup"><span data-stu-id="27c9b-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="27c9b-146">Você deve adicionar um elemento `<CustomDataSignature>` ao elemento `<TemplateData>`.</span><span class="sxs-lookup"><span data-stu-id="27c9b-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="27c9b-147">O elemento `<CustomDataSignature>` deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="27c9b-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="27c9b-148">Você não pode modificar os arquivos em uma pasta compactada (arquivo. zip) diretamente.</span><span class="sxs-lookup"><span data-stu-id="27c9b-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="27c9b-149">Você deve copiar o arquivo. vstemplate da pasta compactada, modificá-lo e, em seguida, substituir o arquivo. vstemplate na pasta compactada por sua cópia atualizada.</span><span class="sxs-lookup"><span data-stu-id="27c9b-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="27c9b-150">O exemplo a seguir mostra o conteúdo de um arquivo. vstemplate que tem o elemento `<CustomDataSignature>` adicionado.</span><span class="sxs-lookup"><span data-stu-id="27c9b-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a><span data-ttu-id="27c9b-151">Instalar o modelo</span><span class="sxs-lookup"><span data-stu-id="27c9b-151">Install the template</span></span>

<span data-ttu-id="27c9b-152">Para instalar o modelo, você pode copiar a pasta compactada (arquivo *. zip* ) para a pasta Visual Basic item templates.</span><span class="sxs-lookup"><span data-stu-id="27c9b-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="27c9b-153">Por padrão, os modelos de item de usuário estão localizados no *%USERPROFILE%\Documents\Visual Studio \<versão\>Basic \Templates\ItemTemplates\Visual*.</span><span class="sxs-lookup"><span data-stu-id="27c9b-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="27c9b-154">Como alternativa, você pode publicar o modelo como um arquivo de Instalador do Visual Studio ( *. VSI*).</span><span class="sxs-lookup"><span data-stu-id="27c9b-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="27c9b-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27c9b-155">See also</span></span>

- [<span data-ttu-id="27c9b-156">Estendendo o Meu Namespace em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27c9b-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="27c9b-157">Estendendo o modelo de aplicativo do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27c9b-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="27c9b-158">Personalizando quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="27c9b-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="27c9b-159">Página Minhas extensões, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="27c9b-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
