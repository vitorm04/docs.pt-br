---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400067"
---
# <a name="para-visual-basic"></a><span data-ttu-id="e9a19-101">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a19-101">\<para> (Visual Basic)</span></span>
<span data-ttu-id="e9a19-102">Especifica que o conteúdo é formatado como um parágrafo.</span><span class="sxs-lookup"><span data-stu-id="e9a19-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a19-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9a19-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9a19-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9a19-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="e9a19-105">O texto do parágrafo.</span><span class="sxs-lookup"><span data-stu-id="e9a19-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9a19-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9a19-106">Remarks</span></span>  
 <span data-ttu-id="e9a19-107">A `<para>` marca é para uso dentro de uma marca, como [\<summary>](summary.md) , [\<remarks>](remarks.md) ou [\<returns>](returns.md) , e permite que você adicione a estrutura ao texto.</span><span class="sxs-lookup"><span data-stu-id="e9a19-107">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="e9a19-108">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e9a19-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9a19-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9a19-109">Example</span></span>  
 <span data-ttu-id="e9a19-110">Este exemplo usa a `<para>` marca para dividir a seção de comentários do `UpdateRecord` método em dois parágrafos.</span><span class="sxs-lookup"><span data-stu-id="e9a19-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e9a19-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9a19-111">See also</span></span>

- [<span data-ttu-id="e9a19-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="e9a19-112">XML Comment Tags</span></span>](index.md)
