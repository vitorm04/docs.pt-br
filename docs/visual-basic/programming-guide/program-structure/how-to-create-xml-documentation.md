---
title: "Como: criar documentação XML no Visual Basic | Documentos do Microsoft"
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
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 3171877f4fa1913b5535d71d671cea97b5a22850
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="6a8ad-102">Como criar documentação XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a8ad-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="6a8ad-103">Este exemplo mostra como adicionar comentários de documentação XML a seu código.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="6a8ad-104">Para criar documentação XML para um tipo ou membro</span><span class="sxs-lookup"><span data-stu-id="6a8ad-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="6a8ad-105">No **Editor de códigos**, posicione o cursor na linha acima do tipo ou membro para o qual você deseja criar documentação.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="6a8ad-106">Tipo de `'''` (três aspas simples).</span><span class="sxs-lookup"><span data-stu-id="6a8ad-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="6a8ad-107">Um esqueleto XML para o tipo ou membro é adicionado a **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="6a8ad-108">Adicione informações descritivas entre as marcas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a8ad-109">Se você adicionar linhas adicionais no bloco de documentação XML, cada linha deve começar com `'''`.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="6a8ad-110">Adicione código adicional que usa o tipo ou membro com os novos comentários de documentação XML.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="6a8ad-111">O IntelliSense exibe o texto do \<resumo > marca para o tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="6a8ad-112">Compile o código para gerar um arquivo XML contendo comentários de documentação.</span><span class="sxs-lookup"><span data-stu-id="6a8ad-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="6a8ad-113">Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="6a8ad-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8ad-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a8ad-114">See Also</span></span>  
 <span data-ttu-id="6a8ad-115">[Documentar seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="6a8ad-115">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="6a8ad-116"> [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="6a8ad-116"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="6a8ad-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span><span class="sxs-lookup"><span data-stu-id="6a8ad-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span></span>
