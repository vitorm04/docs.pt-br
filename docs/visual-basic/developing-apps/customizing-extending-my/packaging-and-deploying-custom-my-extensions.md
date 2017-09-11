---
title: "Empacotando e implantando Minhas extensões (Visual Basic) de personalizadas | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
- My namespace, extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 81483722227873d1b145219ae5c4326d841ff876
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="1cd5d-102">Empacotando e implantando personalizadas extensões My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cd5d-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="1cd5d-103">Visual Basic fornece uma maneira fácil para você implantar seu personalizado `My` extensões do namespace usando modelos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="1cd5d-104">Se você estiver criando um modelo de projeto para o qual o `My` extensões são parte integrante do novo tipo de projeto, você pode apenas incluir seu personalizado `My` código de extensão com o projeto quando você exporta o modelo.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="1cd5d-105">Para obter mais informações sobre como exportar modelos de projeto, consulte [como: criar modelos de projeto](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398).</span><span class="sxs-lookup"><span data-stu-id="1cd5d-105">For more information about exporting project templates, see [How to: Create Project Templates](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398).</span></span>  
  
 <span data-ttu-id="1cd5d-106">Se seu personalizado `My` extensão está em um arquivo de código único, você pode exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="1cd5d-107">Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e comportamentos para seu personalizado `My` extensão em um projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="1cd5d-108">Esses recursos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1cd5d-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="1cd5d-109">Permitindo que os usuários gerenciem seu personalizado `My` extensão o **extensões My** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="1cd5d-110">Adicionando automaticamente seu personalizado `My` extensão quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="1cd5d-111">Ocultando o `My` modelo de item de extensão no **Adicionar Item** caixa de diálogo para que ele não está incluído na lista de itens de projeto.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="1cd5d-112">Este tópico discute como empacotar um personalizado `My` extensão como um modelo de item oculto que possa ser gerenciado a **extensões My** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="1cd5d-113">Personalizado `My` extensão também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="1cd5d-114">Criar uma extensão My namespace</span><span class="sxs-lookup"><span data-stu-id="1cd5d-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="1cd5d-115">A primeira etapa na criação de um pacote de implantação para um personalizado `My` extensão é criar a extensão como um arquivo único de código.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="1cd5d-116">Para obter detalhes e orientação sobre como criar um personalizado `My` extensão, consulte [estendendo o Namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1cd5d-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="1cd5d-117">Exportar uma extensão My namespace como um modelo de item</span><span class="sxs-lookup"><span data-stu-id="1cd5d-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="1cd5d-118">Depois de ter um arquivo de código que inclui seu `My` extensão do namespace, você pode exportar o arquivo de código como um modelo de item do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="1cd5d-119">Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [como: criar modelos de Item](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5).</span><span class="sxs-lookup"><span data-stu-id="1cd5d-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cd5d-120">Se seu `My` extensão do namespace tem uma dependência em um assembly específico, você pode personalizar o modelo de item para instalar automaticamente o `My` quando uma referência a esse assembly for adicionada a extensão do namespace.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="1cd5d-121">Como resultado, você deve excluir essa referência de assembly quando você exportar o arquivo de código como um modelo de item do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="1cd5d-122">Personalizar o modelo de item</span><span class="sxs-lookup"><span data-stu-id="1cd5d-122">Customize the item template</span></span>  
 <span data-ttu-id="1cd5d-123">Você pode habilitar o seu modelo de item a ser gerenciado a partir de **extensões My** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="1cd5d-124">Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="1cd5d-125">Para habilitar essas personalizações, você irá adicionar um novo arquivo, chamado arquivo CustomData, ao seu modelo e, em seguida, adicione um novo elemento para o XML no arquivo. vstemplate.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="1cd5d-126">Adicionar o arquivo CustomData</span><span class="sxs-lookup"><span data-stu-id="1cd5d-126">Add the CustomData file</span></span>  
 <span data-ttu-id="1cd5d-127">O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo. CustomData (o nome do arquivo pode ser definido como qualquer valor significativo para seu modelo) e que contém XML.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="1cd5d-128">O XML no arquivo CustomData instrui o Visual Basic para incluir sua `My` extensão quando os usuários utilizarem o **extensões My** página do Designer de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="1cd5d-129">Opcionalmente, você pode adicionar o `AssemblyFullName>` atributo ao seu arquivo XML CustomData.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="1cd5d-130">Isso instrui o Visual Basic para instalar automaticamente seu personalizado `My` extensão quando uma referência a um assembly específico é adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="1cd5d-131">Você pode usar qualquer editor de texto ou editor XML para criar o arquivo CustomData e, em seguida, adicioná-lo à pasta compactada do seu modelo de item (arquivo. zip).</span><span class="sxs-lookup"><span data-stu-id="1cd5d-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="1cd5d-132">Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que irá adicionar o item de modelo à pasta My Extensions de um projeto do Visual Basic quando uma referência ao assembly Microsoft.VisualBasic.PowerPacks.Vs.dll é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="1cd5d-133">O arquivo CustomData contém um `VBMyExtensionTemplate>` elemento que tenha atributos conforme listado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="1cd5d-134">Atributo</span><span class="sxs-lookup"><span data-stu-id="1cd5d-134">Attribute</span></span>|<span data-ttu-id="1cd5d-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cd5d-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="1cd5d-136">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-136">Required.</span></span> <span data-ttu-id="1cd5d-137">Um identificador exclusivo para a extensão.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-137">A unique identifier for the extension.</span></span> <span data-ttu-id="1cd5d-138">Se a extensão que tiver essa identificação já foi adicionada ao projeto, o usuário não precisará adicioná-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="1cd5d-139">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-139">Required.</span></span> <span data-ttu-id="1cd5d-140">Um número de versão do modelo de item.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="1cd5d-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-141">Optional.</span></span> <span data-ttu-id="1cd5d-142">Um nome de assembly.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-142">An assembly name.</span></span> <span data-ttu-id="1cd5d-143">Quando uma referência a esse assembly é adicionada ao projeto, o usuário será solicitado a adicionar o `My` extensão este modelo de item.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="1cd5d-144">Adicionar o \<CustomDataSignature > elemento para o arquivo. vstemplate</span><span class="sxs-lookup"><span data-stu-id="1cd5d-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="1cd5d-145">Para identificar o seu modelo de item do Visual Studio como um `My` extensão do namespace, você também deve modificar o arquivo. vstemplate para o modelo de item.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="1cd5d-146">Você deve adicionar uma `<CustomDataSignature>` elemento para o `<TemplateData>` elemento.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="1cd5d-147">O `<CustomDataSignature>` elemento deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="1cd5d-148">Você não pode modificar diretamente os arquivos em uma pasta compactada (arquivo. zip).</span><span class="sxs-lookup"><span data-stu-id="1cd5d-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="1cd5d-149">Você deve copiar o arquivo. vstemplate da pasta compactada, modificá-lo e, em seguida, substitua o arquivo. vstemplate na pasta compactada por sua cópia atualizada.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="1cd5d-150">O exemplo a seguir mostra o conteúdo de um arquivo. vstemplate que tem o `<CustomDataSignature>` elemento adicionado.</span><span class="sxs-lookup"><span data-stu-id="1cd5d-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
```  
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
  
## <a name="install-the-template"></a><span data-ttu-id="1cd5d-151">Instalar o modelo</span><span class="sxs-lookup"><span data-stu-id="1cd5d-151">Install the template</span></span>  
 <span data-ttu-id="1cd5d-152">Para instalar o modelo, você pode copiar a pasta compactada (arquivo. zip) para a pasta de modelos de item de Visual Basic (por exemplo, Meus Documentos\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1cd5d-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="1cd5d-153">Como alternativa, você pode publicar o modelo como um arquivo de instalação do Visual Studio (VSI).</span><span class="sxs-lookup"><span data-stu-id="1cd5d-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd5d-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cd5d-154">See also</span></span>  
 <span data-ttu-id="1cd5d-155">[Estendendo o Meu Namespace no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="1cd5d-155">[Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span></span>  
<span data-ttu-id="1cd5d-156"> [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span><span class="sxs-lookup"><span data-stu-id="1cd5d-156"> [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span></span>  
<span data-ttu-id="1cd5d-157"> [Personalizando quais objetos estão disponíveis em meu](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span><span class="sxs-lookup"><span data-stu-id="1cd5d-157"> [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span></span>  
<span data-ttu-id="1cd5d-158"> [Página Minhas extensões, Designer de projeto](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="1cd5d-158"> [My Extensions Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span></span>
