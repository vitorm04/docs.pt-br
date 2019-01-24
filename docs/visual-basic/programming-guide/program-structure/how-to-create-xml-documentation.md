---
title: 'Como: Criar documentação XML no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d67724aad6cd3e7af30531328d85e89937390dd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551361"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="4649f-102">Como: Criar documentação XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4649f-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="4649f-103">Este exemplo mostra como adicionar comentários de documentação XML ao seu código.</span><span class="sxs-lookup"><span data-stu-id="4649f-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="4649f-104">Para criar documentação XML para um tipo ou membro</span><span class="sxs-lookup"><span data-stu-id="4649f-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="4649f-105">No **Editor de códigos**, posicione o cursor na linha acima do tipo ou membro para o qual você deseja criar documentação.</span><span class="sxs-lookup"><span data-stu-id="4649f-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="4649f-106">Tipo `'''` (três aspas simples).</span><span class="sxs-lookup"><span data-stu-id="4649f-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="4649f-107">Um esqueleto XML para o tipo ou membro é adicionado a **Editor de códigos**.</span><span class="sxs-lookup"><span data-stu-id="4649f-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="4649f-108">Adicione informações descritivas entre as marcas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="4649f-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4649f-109">Se você adicionar linhas adicionais no bloco de documentação XML, cada linha deve começar com `'''`.</span><span class="sxs-lookup"><span data-stu-id="4649f-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="4649f-110">Adicione mais código que usa o tipo ou membro com os novos comentários de documentação XML.</span><span class="sxs-lookup"><span data-stu-id="4649f-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="4649f-111">O IntelliSense exibe o texto do \<resumo > marca para o tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="4649f-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="4649f-112">Compile o código para gerar um arquivo XML que contém os comentários de documentação.</span><span class="sxs-lookup"><span data-stu-id="4649f-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="4649f-113">Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="4649f-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4649f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4649f-114">See also</span></span>
- [<span data-ttu-id="4649f-115">Documentando o Código com XML</span><span class="sxs-lookup"><span data-stu-id="4649f-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="4649f-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="4649f-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="4649f-117">/doc</span><span class="sxs-lookup"><span data-stu-id="4649f-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
