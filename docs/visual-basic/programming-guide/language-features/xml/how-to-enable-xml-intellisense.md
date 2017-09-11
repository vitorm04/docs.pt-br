---
title: 'Como: habilitar o XML IntelliSense no Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e367016c93586ad34492628b6a4384a5ef1b6acd
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="75247-102">Como habilitar o IntelliSense XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75247-102">How to: Enable XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="75247-103">XML IntelliSense no Visual Basic fornece preenchimento automático de palavras para os elementos que são definidos em um esquema XML.</span><span class="sxs-lookup"><span data-stu-id="75247-103">XML IntelliSense in Visual Basic provides word completion for elements that are defined in an XML schema.</span></span> <span data-ttu-id="75247-104">Para habilitar o XML IntelliSense no Visual Basic, você deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="75247-104">To enable XML IntelliSense in Visual Basic, you must do the following:</span></span>  
  
1.  <span data-ttu-id="75247-105">Obter o arquivo de esquema (XSD) XML ou arquivos para os arquivos XML que seu aplicativo irá ler ou gravar.</span><span class="sxs-lookup"><span data-stu-id="75247-105">Obtain the XML schema (XSD) file or files for the XML files that your application will read from or write to.</span></span>  
  
2.  <span data-ttu-id="75247-106">Inclua os arquivos de esquema XML em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="75247-106">Include the XML schema files in your project.</span></span>  
  
3.  <span data-ttu-id="75247-107">Importe o namespace de destino ou espaços para nome para seu arquivo de código ou projeto.</span><span class="sxs-lookup"><span data-stu-id="75247-107">Import the target namespace or namespaces into your code file or project.</span></span> <span data-ttu-id="75247-108">Um namespace de destino é identificado pelo `targetNamespace` ou `tns` atributo do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="75247-108">A target namespace is identified by the `targetNamespace` or `tns` attribute of your XSD schema.</span></span>  
  
     <span data-ttu-id="75247-109">Para importar um namespace de destino, use o `Imports` instrução, ou adicionar um namespace para todos os arquivos de código em um projeto usando o **referências** página do Project Designer.</span><span class="sxs-lookup"><span data-stu-id="75247-109">To import a target namespace, use the `Imports` statement, or add a namespace for all code files in a project by using the **References** page of the Project Designer.</span></span>  
  
 <span data-ttu-id="75247-110">Para obter mais informações sobre os recursos do IntelliSense XML no Visual Basic, consulte [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).</span><span class="sxs-lookup"><span data-stu-id="75247-110">For more information on the capabilities of XML IntelliSense in Visual Basic, see [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).</span></span> <span data-ttu-id="75247-111">Para obter mais informações sobre como importar namespaces XML, consulte [instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) ou [referências de página, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="75247-111">For more information on importing XML namespaces, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) or [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="75247-112">![link para vídeo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") para uma versão em vídeo deste tópico, consulte [vídeo como: habilitar o XML IntelliSense no Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466).</span><span class="sxs-lookup"><span data-stu-id="75247-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For a video version of this topic, see [Video How to: Enable XML IntelliSense in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466).</span></span> <span data-ttu-id="75247-113">Para uma demonstração em vídeo relacionada, consulte [como faço para habilitar XML IntelliSense e Namespaces de XML de uso?](http://go.microsoft.com/fwlink/?LinkId=143035).</span><span class="sxs-lookup"><span data-stu-id="75247-113">For a related video demonstration, see [How Do I Enable XML IntelliSense and Use XML Namespaces?](http://go.microsoft.com/fwlink/?LinkId=143035).</span></span>  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="75247-114">Habilitar o IntelliSense XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75247-114">Enable XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="75247-115">Se você tiver um arquivo XML, mas você não tem um arquivo de esquema XSD para ele, no SP1 você pode criar um arquivo de esquema XSD usando o Assistente de XML para esquema.</span><span class="sxs-lookup"><span data-stu-id="75247-115">If you have an XML file but you do not have an XSD schema file for it, in SP1 you can create an XSD schema file by using the XML to Schema Wizard.</span></span> <span data-ttu-id="75247-116">Você também pode usar inferência de esquema no Editor de XML do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75247-116">You can also use schema inference in the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a><span data-ttu-id="75247-117">Para criar um arquivo de esquema XSD para um arquivo XML usando o Assistente de XML para esquema (requer SP1)</span><span class="sxs-lookup"><span data-stu-id="75247-117">To create an XSD schema file for an XML file by using the XML to Schema Wizard (requires SP1)</span></span>  
  
1.  <span data-ttu-id="75247-118">Em seu projeto, clique em **Adicionar Novo Item** sobre o **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="75247-118">In your project, click **Add New Item** on the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="75247-119">Selecione o **Xml para esquema** modelo de item do **dados** ou **itens comuns** categorias de modelo.</span><span class="sxs-lookup"><span data-stu-id="75247-119">Select the **Xml to Schema** item template from either the **Data** or **Common Items** template categories.</span></span>  
  
3.  <span data-ttu-id="75247-120">Forneça um nome de arquivo para o arquivo XSD ou arquivos que o conjunto de esquema inferido serão armazenados em e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="75247-120">Provide a file name for the XSD file or files that the inferred schema set will be stored in, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="75247-121">No **inferir esquema XML definido de documentos XML** janela, adicione um ou mais documentos XML para inferir o esquema XML definido de.</span><span class="sxs-lookup"><span data-stu-id="75247-121">In the **Infer XML Schema set from XML documents** window, add one or more XML documents to infer the XML schema set from.</span></span>  
  
    -   <span data-ttu-id="75247-122">Para adicionar arquivos de texto que contêm documentos XML usando o Explorador de arquivos, clique em **adicionar de arquivo**.</span><span class="sxs-lookup"><span data-stu-id="75247-122">To add text files that contain XML documents by using File Explorer, click **Add from File**.</span></span>  
  
    -   <span data-ttu-id="75247-123">Para adicionar um documento XML de um endereço HTTP, clique em **adicionar da Web**.</span><span class="sxs-lookup"><span data-stu-id="75247-123">To add an XML document from an HTTP address, click **Add from Web**.</span></span>  
  
    -   <span data-ttu-id="75247-124">Para copiar ou digitar o conteúdo de um documento XML no assistente, clique em **digitar ou colar XML**.</span><span class="sxs-lookup"><span data-stu-id="75247-124">To copy or type the contents of an XML document into the wizard, click **Type or paste XML**.</span></span>  
  
5.  <span data-ttu-id="75247-125">Quando você tiver especificado todas as fontes de documento XML do qual você deseja inferir o conjunto de esquema XML, clique em **Okey** inferir o esquema XML definido.</span><span class="sxs-lookup"><span data-stu-id="75247-125">When you have specified all the XML document sources from which you want to infer the XML schema set, click **OK** to infer the XML schema set.</span></span> <span data-ttu-id="75247-126">O conjunto de esquema é salvo na pasta do projeto em um ou mais arquivos XSD.</span><span class="sxs-lookup"><span data-stu-id="75247-126">The schema set is saved in your project folder in one or more XSD files.</span></span> <span data-ttu-id="75247-127">(Para cada namespace XML no esquema, um arquivo é criado.)</span><span class="sxs-lookup"><span data-stu-id="75247-127">(For each XML namespace in the schema, a file is created.)</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a><span data-ttu-id="75247-128">Para criar um arquivo de esquema XSD para um arquivo XML usando inferência de esquema no Editor de XML do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="75247-128">To create an XSD schema file for an XML file by using schema inference in the Visual Studio XML Editor</span></span>  
  
1.  <span data-ttu-id="75247-129">Edite o arquivo XML Designer XML do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75247-129">Edit the XML file in the Visual Studio XML Designer.</span></span>  
  
2.  <span data-ttu-id="75247-130">Quando o cursor estiver em algum lugar no arquivo XML, o **XML** menu é exibido.</span><span class="sxs-lookup"><span data-stu-id="75247-130">When the cursor is somewhere in the XML file, the **XML** menu appears.</span></span> <span data-ttu-id="75247-131">Clique em **Create Schema** sobre o **XML** menu.</span><span class="sxs-lookup"><span data-stu-id="75247-131">Click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="75247-132">É criado um arquivo XSD do esquema XSD inferida do arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="75247-132">An XSD file is created from XSD schema inferred from the XML file.</span></span>  
  
3.  <span data-ttu-id="75247-133">Salve o arquivo de esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="75247-133">Save the XSD schema file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75247-134">Diferentes esquemas XSD podem ser inferidas de vários documentos XML que devem ter o mesmo esquema.</span><span class="sxs-lookup"><span data-stu-id="75247-134">Different XSD schemas might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="75247-135">Isso pode ocorrer quando determinados elementos e atributos são encontrados em um arquivo XML e não no outro, ou quando estiver incluído em uma ordem diferente, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="75247-135">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="75247-136">Você deve revisar esquemas XSD inferidos para a integridade e a precisão quando você usa a inferência de esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="75247-136">You should review inferred XSD schemas for completeness and accuracy when you use XSD schema inference.</span></span>  
  
#### <a name="to-include-an-xsd-schema-file"></a><span data-ttu-id="75247-137">Para incluir um arquivo de esquema XSD</span><span class="sxs-lookup"><span data-stu-id="75247-137">To include an XSD schema file</span></span>  
  
-   <span data-ttu-id="75247-138">Por padrão, é possível ver os arquivos XSD em projetos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="75247-138">By default, you cannot see XSD files in Visual Basic projects.</span></span> <span data-ttu-id="75247-139">Se o arquivo XSD já está incluído nas pastas de seu projeto, clique o **Show All Files** no botão **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="75247-139">If your XSD file is already included in the folders for your project, click the **Show All Files** button in **Solution Explorer**.</span></span> <span data-ttu-id="75247-140">Localize o arquivo XSD em **Solution Explorer**, clique no arquivo e clique em **incluir o arquivo no projeto**.</span><span class="sxs-lookup"><span data-stu-id="75247-140">Locate the XSD file in **Solution Explorer**, right-click the file, and click **Include File in Project**.</span></span>  
  
-   <span data-ttu-id="75247-141">Se o arquivo XSD já não é parte do seu projeto, em **Solution Explorer**, clique na pasta na qual você deseja armazenar o arquivo XSD, aponte para **adicionar**e, em seguida, clique em **Item existente**.</span><span class="sxs-lookup"><span data-stu-id="75247-141">If your XSD file is not already part of your project, in **Solution Explorer**, right-click the folder in which you want to store the XSD file, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="75247-142">Localize o arquivo XSD e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="75247-142">Locate your XSD file and then click **Add**.</span></span>  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a><span data-ttu-id="75247-143">Para importar um namespace XML em um arquivo de código</span><span class="sxs-lookup"><span data-stu-id="75247-143">To import an XML namespace in a code file</span></span>  
  
1.  <span data-ttu-id="75247-144">Identifique o namespace de destino do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="75247-144">Identify the target namespace from your XSD schema.</span></span>  
  
2.  <span data-ttu-id="75247-145">No início do arquivo de código, adicione um `Imports` declaração para o namespace XML de destino, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="75247-145">At the beginning of the code file, add an `Imports` statement for the target XML namespace, as shown in the following example.</span></span>  
  
     <span data-ttu-id="75247-146">[!code-vb[VbXMLSamples n º&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="75247-146">[!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span></span>  
  
     <span data-ttu-id="75247-147">Para importar um namespace XML como o namespace padrão, ou seja, o namespace que é aplicado a elementos XML e atributos que não têm um prefixo de namespace, adicione um `Imports` declaração do namespace de destino padrão XML.</span><span class="sxs-lookup"><span data-stu-id="75247-147">To import an XML namespace as the default namespace, that is, the namespace that is applied to XML elements and attributes that do not have a namespace prefix, add an `Imports` statement for the target default XML namespace.</span></span> <span data-ttu-id="75247-148">Não especifique um prefixo de namespace.</span><span class="sxs-lookup"><span data-stu-id="75247-148">Do not specify a namespace prefix.</span></span> <span data-ttu-id="75247-149">A seguir está um exemplo de uma `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="75247-149">Following is an example of an `Imports` statement.</span></span>  
  
     <span data-ttu-id="75247-150">[!code-vb[VbXmlSamples&#50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="75247-150">[!code-vb[VbXmlSamples#50](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span></span>  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a><span data-ttu-id="75247-151">Para importar um namespace XML para todos os arquivos em um projeto</span><span class="sxs-lookup"><span data-stu-id="75247-151">To import an XML namespace for all files in a project</span></span>  
  
1.  <span data-ttu-id="75247-152">Um namespace XML importado em um arquivo de código aplica-se somente nesse arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="75247-152">An XML namespace imported in a code file applies to that code file only.</span></span> <span data-ttu-id="75247-153">Para importar um namespace XML que se aplica a todos os arquivos de código em um projeto, abra o Project Designer clicando duas vezes em **meu projeto** na **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="75247-153">To import an XML namespace that applies to all code files in a project, open the Project Designer by double-clicking **My Project** in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="75247-154">Sobre o **referências** guia o **importado namespaces** , digite o namespace de XML de destino na forma de uma declaração de namespace XML completa (por exemplo, `<xmlns: ns="http://sampleNamespace">`).</span><span class="sxs-lookup"><span data-stu-id="75247-154">On the **References** tab, in the **Imported namespaces** box, type the target XML namespace in the form of a full XML namespace declaration (for example, `<xmlns: ns="http://sampleNamespace">`).</span></span> <span data-ttu-id="75247-155">Se o namespace de XML de destino não especificar um prefixo de namespace, o namespace será o namespace XML padrão para o projeto.</span><span class="sxs-lookup"><span data-stu-id="75247-155">If the target XML namespace does not specify a namespace prefix, the namespace will be the default XML namespace for the project.</span></span>  
  
3.  <span data-ttu-id="75247-156">Clique em **Adicionar importação de usuário**.</span><span class="sxs-lookup"><span data-stu-id="75247-156">Click **Add User Import**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75247-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75247-157">See Also</span></span>  
 <span data-ttu-id="75247-158">[Instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="75247-158">[Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="75247-159"> [Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="75247-159"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="75247-160"> [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span><span class="sxs-lookup"><span data-stu-id="75247-160"> [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span></span>

