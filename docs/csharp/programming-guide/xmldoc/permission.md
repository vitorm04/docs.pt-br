---
title: <permission> – Guia de Programação em C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 67e9d398d1bb43d480f8ca56733106e0f0a22731
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696565"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="1ba05-102">\<permission> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1ba05-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1ba05-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ba05-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ba05-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ba05-104">Parameters</span></span>  
 <span data-ttu-id="1ba05-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="1ba05-105">cref = " `member`"</span></span>  
 <span data-ttu-id="1ba05-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="1ba05-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1ba05-107">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="1ba05-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="1ba05-108">*member* deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="1ba05-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="1ba05-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [\<consulte>](./see.md).</span><span class="sxs-lookup"><span data-stu-id="1ba05-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="1ba05-110">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="1ba05-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ba05-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ba05-111">Remarks</span></span>  
 <span data-ttu-id="1ba05-112">A marca \<permissão > permite documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="1ba05-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="1ba05-113">A classe <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="1ba05-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="1ba05-114">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="1ba05-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ba05-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ba05-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="1ba05-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="1ba05-116">See also</span></span>

- [<span data-ttu-id="1ba05-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1ba05-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1ba05-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="1ba05-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
