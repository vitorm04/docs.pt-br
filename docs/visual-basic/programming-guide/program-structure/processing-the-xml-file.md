---
title: Processando o arquivo XML (Visual Basic) | Documentos do Microsoft
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
- XML comments, parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
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
ms.openlocfilehash: cf15cf59413e0e019086dd1a79951ccb212f037b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="97f0b-102">Processando o arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97f0b-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="97f0b-103">O compilador gera uma cadeia de caracteres de identificação para cada constructo no seu código marcado para gerar a documentação.</span><span class="sxs-lookup"><span data-stu-id="97f0b-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="97f0b-104">(Para obter informações sobre como marcar seu código, consulte [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) A cadeia de caracteres de identificação identifica exclusivamente o constructo.</span><span class="sxs-lookup"><span data-stu-id="97f0b-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="97f0b-105">Programas que processam o arquivo XML podem usar a cadeia de caracteres de identificação para identificar o correspondente [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] item metadados/reflexão.</span><span class="sxs-lookup"><span data-stu-id="97f0b-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="97f0b-106">O arquivo XML não é uma representação hierárquica de seu código; é uma lista simples com uma identificação gerada para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="97f0b-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="97f0b-107">O compilador observa as regras a seguir quando ele gera as cadeias de caracteres de ID:</span><span class="sxs-lookup"><span data-stu-id="97f0b-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="97f0b-108">Nenhum espaço em branco é colocado na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="97f0b-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="97f0b-109">A primeira parte da cadeia de caracteres de identificação identifica o tipo de membro está sendo identificado, com um único caractere seguido por dois pontos.</span><span class="sxs-lookup"><span data-stu-id="97f0b-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="97f0b-110">Os seguintes tipos de membro são usados.</span><span class="sxs-lookup"><span data-stu-id="97f0b-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="97f0b-111">Caractere</span><span class="sxs-lookup"><span data-stu-id="97f0b-111">Character</span></span>|<span data-ttu-id="97f0b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="97f0b-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="97f0b-113">N</span><span class="sxs-lookup"><span data-stu-id="97f0b-113">N</span></span>|<span data-ttu-id="97f0b-114">namespace</span><span class="sxs-lookup"><span data-stu-id="97f0b-114">namespace</span></span><br /><br /> <span data-ttu-id="97f0b-115">Não é possível adicionar comentários de documentação a um namespace, mas você pode fazer referências CREF a eles, onde há suporte.</span><span class="sxs-lookup"><span data-stu-id="97f0b-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="97f0b-116">T</span><span class="sxs-lookup"><span data-stu-id="97f0b-116">T</span></span>|<span data-ttu-id="97f0b-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`</span><span class="sxs-lookup"><span data-stu-id="97f0b-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="97f0b-118">F</span><span class="sxs-lookup"><span data-stu-id="97f0b-118">F</span></span>|<span data-ttu-id="97f0b-119">campo:`Dim`</span><span class="sxs-lookup"><span data-stu-id="97f0b-119">field: `Dim`</span></span>|  
|<span data-ttu-id="97f0b-120">P</span><span class="sxs-lookup"><span data-stu-id="97f0b-120">P</span></span>|<span data-ttu-id="97f0b-121">propriedade: `Property` (incluindo propriedades padrão)</span><span class="sxs-lookup"><span data-stu-id="97f0b-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="97f0b-122">M</span><span class="sxs-lookup"><span data-stu-id="97f0b-122">M</span></span>|<span data-ttu-id="97f0b-123">method: `Sub`, `Function`, `Declare`,`Operator`</span><span class="sxs-lookup"><span data-stu-id="97f0b-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="97f0b-124">E</span><span class="sxs-lookup"><span data-stu-id="97f0b-124">E</span></span>|<span data-ttu-id="97f0b-125">evento:`Event`</span><span class="sxs-lookup"><span data-stu-id="97f0b-125">event: `Event`</span></span>|  
|<span data-ttu-id="97f0b-126">!</span><span class="sxs-lookup"><span data-stu-id="97f0b-126">!</span></span>|<span data-ttu-id="97f0b-127">cadeia de caracteres de erro</span><span class="sxs-lookup"><span data-stu-id="97f0b-127">error string</span></span><br /><br /> <span data-ttu-id="97f0b-128">O restante da cadeia de caracteres fornece informações sobre o erro.</span><span class="sxs-lookup"><span data-stu-id="97f0b-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="97f0b-129">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador gera informações de erro para links que não podem ser resolvidos.</span><span class="sxs-lookup"><span data-stu-id="97f0b-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="97f0b-130">A segunda parte do `String` é o nome totalmente qualificado do item, iniciando na raiz do namespace.</span><span class="sxs-lookup"><span data-stu-id="97f0b-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="97f0b-131">O nome do item, seus tipos delimitador e o namespace são separados por pontos.</span><span class="sxs-lookup"><span data-stu-id="97f0b-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="97f0b-132">Se o nome do próprio item contiver períodos, eles serão substituídos pelo sinal numérico (#).</span><span class="sxs-lookup"><span data-stu-id="97f0b-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="97f0b-133">Supõe-se que nenhum item possui um sinal de número diretamente no seu nome.</span><span class="sxs-lookup"><span data-stu-id="97f0b-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="97f0b-134">Por exemplo, o nome totalmente qualificado do `String` construtor seria `System.String.#ctor`.</span><span class="sxs-lookup"><span data-stu-id="97f0b-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="97f0b-135">Para propriedades e métodos, se houver argumentos para o método, segue a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="97f0b-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="97f0b-136">Se não houver nenhum argumento, nenhum parêntese estará presente.</span><span class="sxs-lookup"><span data-stu-id="97f0b-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="97f0b-137">Os argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="97f0b-137">The arguments are separated by commas.</span></span> <span data-ttu-id="97f0b-138">A codificação de cada argumento segue diretamente como ela é codificada em um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assinatura.</span><span class="sxs-lookup"><span data-stu-id="97f0b-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97f0b-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97f0b-139">Example</span></span>  
 <span data-ttu-id="97f0b-140">O código a seguir mostra como a ID de cadeias de caracteres para uma classe e seus membros são gerados.</span><span class="sxs-lookup"><span data-stu-id="97f0b-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 <span data-ttu-id="97f0b-141">[!code-vb[VbVbcnXmlDocComments n º&10;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="97f0b-141">[!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f0b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97f0b-142">See Also</span></span>  
 <span data-ttu-id="97f0b-143">[/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span><span class="sxs-lookup"><span data-stu-id="97f0b-143">[/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span></span>  
<span data-ttu-id="97f0b-144"> [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="97f0b-144"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span></span>
