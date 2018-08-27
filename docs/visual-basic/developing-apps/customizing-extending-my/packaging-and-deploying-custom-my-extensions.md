---
title: Empacotando e implantando personalizadas extensões My (Visual Basic)
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931486"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="9e534-102">Empacotar e implantar personalizado extensões My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e534-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="9e534-103">Visual Basic fornece uma maneira fácil para você implantar o personalizado `My` extensões do namespace usando modelos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e534-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="9e534-104">Se você estiver criando um modelo de projeto para o qual sua `My` extensões são parte integrante do novo tipo de projeto, você pode apenas incluir seu personalizado `My` código de extensão com o projeto quando você exporta o modelo.</span><span class="sxs-lookup"><span data-stu-id="9e534-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="9e534-105">Para obter mais informações sobre como exportar modelos de projeto, consulte [como: criar modelos de projeto](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="9e534-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="9e534-106">Se seu personalizado `My` extensão está em um arquivo de código único, você pode exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e534-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="9e534-107">Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e o comportamento para o personalizado `My` extensão em um projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e534-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="9e534-108">Esses recursos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9e534-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="9e534-109">Permitindo que os usuários gerenciem seu personalizado `My` extensão do **Minhas extensões** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e534-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="9e534-110">Adicionando automaticamente seu personalizado `My` extensão quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="9e534-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="9e534-111">Ocultando o `My` modelo de item de extensão na **Add Item** caixa de diálogo para que ele não está incluído na lista de itens de projeto.</span><span class="sxs-lookup"><span data-stu-id="9e534-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="9e534-112">Este tópico discute como empacotar um personalizado `My` extensão como um modelo de item oculto que pode ser gerenciado do **Minhas extensões** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e534-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="9e534-113">Personalizado `My` extensão também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="9e534-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="9e534-114">Criar uma extensão My namespace</span><span class="sxs-lookup"><span data-stu-id="9e534-114">Create a My namespace extension</span></span>

<span data-ttu-id="9e534-115">A primeira etapa na criação de um pacote de implantação personalizado `My` extensão é criar a extensão como um arquivo de código único.</span><span class="sxs-lookup"><span data-stu-id="9e534-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="9e534-116">Para obter detalhes e orientações sobre como criar um personalizado `My` extensão, consulte [estendendo o Namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9e534-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="9e534-117">Exportar uma extensão My namespace como um modelo de item</span><span class="sxs-lookup"><span data-stu-id="9e534-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="9e534-118">Depois que você tiver um arquivo de código que inclui seu `My` extensão do namespace, você pode exportar o arquivo de código como um modelo de item do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e534-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="9e534-119">Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [como: criar modelos de Item](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="9e534-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="9e534-120">Se sua `My` extensão do namespace tem uma dependência em um assembly específico, você pode personalizar seu modelo de item para instalar automaticamente seu `My` quando uma referência a esse assembly é adicionada a extensão do namespace.</span><span class="sxs-lookup"><span data-stu-id="9e534-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="9e534-121">Como resultado, você desejará excluir essa referência de assembly quando você exportar o arquivo de código como um modelo de item do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e534-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="9e534-122">Personalizar o modelo de item</span><span class="sxs-lookup"><span data-stu-id="9e534-122">Customize the item template</span></span>

<span data-ttu-id="9e534-123">Você pode habilitar o seu modelo de item a ser gerenciados a partir de **Minhas extensões** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e534-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="9e534-124">Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="9e534-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="9e534-125">Para habilitar essas personalizações, você irá adicionar um novo arquivo chamado arquivo CustomData, ao seu modelo e, em seguida, adicione um novo elemento ao XML em seu arquivo. vstemplate.</span><span class="sxs-lookup"><span data-stu-id="9e534-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="9e534-126">Adicione o arquivo CustomData</span><span class="sxs-lookup"><span data-stu-id="9e534-126">Add the CustomData file</span></span>

<span data-ttu-id="9e534-127">O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo. CustomData (o nome do arquivo pode ser definido como qualquer valor significativo ao seu modelo) e que contém XML.</span><span class="sxs-lookup"><span data-stu-id="9e534-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="9e534-128">O XML no arquivo CustomData instrui o Visual Basic para incluir sua `My` extensão quando os usuários usam o **Minhas extensões** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e534-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="9e534-129">Opcionalmente, você pode adicionar o <`AssemblyFullName>` de atributo para o seu arquivo XML CustomData.</span><span class="sxs-lookup"><span data-stu-id="9e534-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="9e534-130">Isso instrui o Visual Basic para instalar automaticamente seu personalizado `My` quando uma referência a um assembly específico de extensão é adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9e534-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="9e534-131">Você pode usar qualquer editor de texto ou editor XML para criar o arquivo CustomData e, em seguida, adicioná-lo para a pasta compactada do seu modelo item (arquivo. zip).</span><span class="sxs-lookup"><span data-stu-id="9e534-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="9e534-132">Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que irá adicionar o item de modelo para a pasta Minhas extensões de um projeto do Visual Basic quando uma referência ao assembly Microsoft.VisualBasic.PowerPacks.Vs.dll é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9e534-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="9e534-133">O arquivo CustomData contém um <`VBMyExtensionTemplate>` elemento que tem atributos conforme listado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="9e534-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="9e534-134">Atributo</span><span class="sxs-lookup"><span data-stu-id="9e534-134">Attribute</span></span>|<span data-ttu-id="9e534-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e534-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="9e534-136">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9e534-136">Required.</span></span> <span data-ttu-id="9e534-137">Um identificador exclusivo para a extensão.</span><span class="sxs-lookup"><span data-stu-id="9e534-137">A unique identifier for the extension.</span></span> <span data-ttu-id="9e534-138">Se a extensão que tem essa ID já foi adicionada ao projeto, o usuário não precisará adicioná-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="9e534-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="9e534-139">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9e534-139">Required.</span></span> <span data-ttu-id="9e534-140">Um número de versão para o modelo de item.</span><span class="sxs-lookup"><span data-stu-id="9e534-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="9e534-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9e534-141">Optional.</span></span> <span data-ttu-id="9e534-142">Um nome de assembly.</span><span class="sxs-lookup"><span data-stu-id="9e534-142">An assembly name.</span></span> <span data-ttu-id="9e534-143">Quando uma referência a esse assembly é adicionada ao projeto, o usuário será solicitado a adicionar o `My` extensão com base neste modelo de item.</span><span class="sxs-lookup"><span data-stu-id="9e534-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="9e534-144">Adicionar o \<CustomDataSignature > elemento para o arquivo. vstemplate</span><span class="sxs-lookup"><span data-stu-id="9e534-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="9e534-145">Para identificar o modelo de item do Visual Studio como um `My` extensão do namespace, você também deve modificar o arquivo. vstemplate para o modelo de item.</span><span class="sxs-lookup"><span data-stu-id="9e534-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="9e534-146">Você deve adicionar uma `<CustomDataSignature>` elemento para o `<TemplateData>` elemento.</span><span class="sxs-lookup"><span data-stu-id="9e534-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="9e534-147">O `<CustomDataSignature>` elemento deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9e534-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="9e534-148">Você não pode modificar diretamente os arquivos em uma pasta compactada (arquivo. zip).</span><span class="sxs-lookup"><span data-stu-id="9e534-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="9e534-149">Você deve copiar o arquivo. vstemplate da pasta compactada, modificá-lo e, em seguida, substitua o arquivo. vstemplate na pasta compactada com a cópia atualizada.</span><span class="sxs-lookup"><span data-stu-id="9e534-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="9e534-150">O exemplo a seguir mostra o conteúdo de um arquivo. vstemplate que tem o `<CustomDataSignature>` elemento adicionado.</span><span class="sxs-lookup"><span data-stu-id="9e534-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="9e534-151">Instalar o modelo</span><span class="sxs-lookup"><span data-stu-id="9e534-151">Install the template</span></span>

<span data-ttu-id="9e534-152">Para instalar o modelo, você pode copiar a pasta compactada (*. zip* arquivo) para a pasta de modelos de item do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e534-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="9e534-153">Por padrão, os modelos de item de usuário estão localizados na *%USERPROFILE%\Documents\Visual Studio \<versão\>\Templates\ItemTemplates\Visual Basic*.</span><span class="sxs-lookup"><span data-stu-id="9e534-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="9e534-154">Como alternativa, você pode publicar o modelo como um instalador do Visual Studio (*vsi*) arquivos.</span><span class="sxs-lookup"><span data-stu-id="9e534-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e534-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e534-155">See also</span></span>

- [<span data-ttu-id="9e534-156">Estendendo o Meu Namespace em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e534-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="9e534-157">Estendendo o modelo de aplicativo do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e534-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="9e534-158">Personalizando quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="9e534-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="9e534-159">Página Minhas extensões, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="9e534-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
