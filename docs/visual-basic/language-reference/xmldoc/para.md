---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 96ef62d53fd1cc806c0dc72d2d0781b1c6297dc6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970864"
---
# <a name="para-visual-basic"></a><span data-ttu-id="f8af3-102">\<para > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8af3-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="f8af3-103">Especifica que o conteúdo é formatado como um parágrafo.</span><span class="sxs-lookup"><span data-stu-id="f8af3-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8af3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8af3-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8af3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8af3-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="f8af3-106">O texto do parágrafo.</span><span class="sxs-lookup"><span data-stu-id="f8af3-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8af3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8af3-107">Remarks</span></span>  
 <span data-ttu-id="f8af3-108">O `<para>` marca é para uso dentro de uma marca, como [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), ou [ \<retorna >](../../../visual-basic/language-reference/xmldoc/returns.md), e permite que você adicione estrutura ao texto.</span><span class="sxs-lookup"><span data-stu-id="f8af3-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="f8af3-109">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f8af3-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8af3-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8af3-110">Example</span></span>  
 <span data-ttu-id="f8af3-111">Este exemplo usa o `<para>` marca para dividir a seção comentários para o `UpdateRecord` método em dois parágrafos.</span><span class="sxs-lookup"><span data-stu-id="f8af3-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f8af3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8af3-112">See also</span></span>
- [<span data-ttu-id="f8af3-113">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f8af3-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
