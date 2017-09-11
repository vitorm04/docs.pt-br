---
title: "Documentar seu código com XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML, documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
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
ms.openlocfilehash: 0ce3f216f9e851feb0b3506b6ed1279b7d9479e7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="4789d-102">Documentando o código com XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4789d-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="4789d-103">Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você pode documentar seu código usando XML</span><span class="sxs-lookup"><span data-stu-id="4789d-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="4789d-104">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="4789d-104">XML Documentation Comments</span></span>  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4789d-105">Fornece uma maneira fácil de automaticamente criar documentação XML para projetos.</span><span class="sxs-lookup"><span data-stu-id="4789d-105"> provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="4789d-106">Você pode gerar automaticamente um esqueleto XML para seus tipos e membros e, em seguida, fornecer resumos, documentação descritiva para cada parâmetro e outros comentários.</span><span class="sxs-lookup"><span data-stu-id="4789d-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="4789d-107">Com a configuração apropriada, a documentação XML é emitida automaticamente em um arquivo XML com o mesmo nome do projeto e a extensão. XML.</span><span class="sxs-lookup"><span data-stu-id="4789d-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="4789d-108">Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="4789d-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="4789d-109">O arquivo XML pode ser consumido ou manipulado como XML.</span><span class="sxs-lookup"><span data-stu-id="4789d-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="4789d-110">Esse arquivo está localizado no mesmo diretório que o arquivo de saída .exe ou. dll do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4789d-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="4789d-111">Documentação XML começa com `'''`.</span><span class="sxs-lookup"><span data-stu-id="4789d-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="4789d-112">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="4789d-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="4789d-113">A documentação deve ser bem formada XML.</span><span class="sxs-lookup"><span data-stu-id="4789d-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="4789d-114">Se o XML não está bem formado, um aviso será gerado e o arquivo de documentação contém um comentário dizendo que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="4789d-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="4789d-115">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="4789d-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="4789d-116">Há um conjunto recomendado das marcas (consulte "Seções relacionadas" neste tópico).</span><span class="sxs-lookup"><span data-stu-id="4789d-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="4789d-117">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="4789d-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="4789d-118">O \<param > marca é usada para descrever os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4789d-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="4789d-119">Se usado, o compilador verificará se o parâmetro existe e que todos os parâmetros estão descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="4789d-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="4789d-120">Se a verificação falhar, o compilador emite um aviso.</span><span class="sxs-lookup"><span data-stu-id="4789d-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="4789d-121">O `cref` atributo pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="4789d-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="4789d-122">O compilador verifica se este elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="4789d-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="4789d-123">Se a verificação falhar, o compilador emite um aviso.</span><span class="sxs-lookup"><span data-stu-id="4789d-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="4789d-124">O compilador também respeita qualquer `Imports` instruções ao procurar por um tipo descrito o `cref` atributo.</span><span class="sxs-lookup"><span data-stu-id="4789d-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="4789d-125">O \<resumo > marca é usada pelo IntelliSense no [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="4789d-125">The \<summary> tag is used by IntelliSense in [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4789d-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="4789d-126">Related Sections</span></span>  
 <span data-ttu-id="4789d-127">Para obter detalhes sobre como criar um arquivo XML com comentários de documentação, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="4789d-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="4789d-128">/doc</span><span class="sxs-lookup"><span data-stu-id="4789d-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="4789d-129">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="4789d-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="4789d-130">Processando o Arquivo XML</span><span class="sxs-lookup"><span data-stu-id="4789d-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="4789d-131">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="4789d-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="4789d-132">Ferramentas XML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4789d-132">XML Tools in Visual Studio</span></span>](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="4789d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4789d-133">See Also</span></span>  
 <span data-ttu-id="4789d-134">[Desenvolvendo aplicativos com o Visual Basic](../../../visual-basic/developing-apps/index.md) </span><span class="sxs-lookup"><span data-stu-id="4789d-134">[Developing Applications with Visual Basic](../../../visual-basic/developing-apps/index.md) </span></span>  
<span data-ttu-id="4789d-135"> [Guia de programação em Visual Basic](../../../visual-basic/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="4789d-135"> [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)</span></span>
