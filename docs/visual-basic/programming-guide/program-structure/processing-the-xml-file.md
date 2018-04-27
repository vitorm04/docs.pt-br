---
title: Processando o arquivo XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 86dae99f2d17a506a27cf491a76083df618ba27b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="39c00-102">Processando o arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39c00-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="39c00-103">O compilador gera uma cadeia de identificação para cada constructo no seu código marcado para gerar a documentação.</span><span class="sxs-lookup"><span data-stu-id="39c00-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="39c00-104">(Para obter informações sobre como marcar seu código, consulte [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) A cadeia de identificação identifica exclusivamente o constructo.</span><span class="sxs-lookup"><span data-stu-id="39c00-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="39c00-105">Programas que processam o arquivo XML podem usar a cadeia de caracteres de ID para identificar correspondente [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] item metadados/reflexão.</span><span class="sxs-lookup"><span data-stu-id="39c00-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="39c00-106">O arquivo XML não é uma representação hierárquica de seu código; é uma lista simples com uma identificação gerada para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="39c00-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="39c00-107">O compilador observa as seguintes regras quando gera as cadeias de identificação:</span><span class="sxs-lookup"><span data-stu-id="39c00-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="39c00-108">Nenhum espaço em branco é colocado na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="39c00-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="39c00-109">A primeira parte da cadeia de caracteres de identificação identifica o tipo de membro identificado, com um único caractere seguido por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="39c00-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="39c00-110">Os seguintes tipos de membro são usados.</span><span class="sxs-lookup"><span data-stu-id="39c00-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="39c00-111">Caractere</span><span class="sxs-lookup"><span data-stu-id="39c00-111">Character</span></span>|<span data-ttu-id="39c00-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="39c00-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="39c00-113">N</span><span class="sxs-lookup"><span data-stu-id="39c00-113">N</span></span>|<span data-ttu-id="39c00-114">namespace</span><span class="sxs-lookup"><span data-stu-id="39c00-114">namespace</span></span><br /><br /> <span data-ttu-id="39c00-115">Você não pode adicionar comentários de documentação para um namespace, mas você pode fazer referências CREF a eles, onde houver suporte.</span><span class="sxs-lookup"><span data-stu-id="39c00-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="39c00-116">T</span><span class="sxs-lookup"><span data-stu-id="39c00-116">T</span></span>|<span data-ttu-id="39c00-117">tipo: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span><span class="sxs-lookup"><span data-stu-id="39c00-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="39c00-118">F</span><span class="sxs-lookup"><span data-stu-id="39c00-118">F</span></span>|<span data-ttu-id="39c00-119">campo: `Dim`</span><span class="sxs-lookup"><span data-stu-id="39c00-119">field: `Dim`</span></span>|  
|<span data-ttu-id="39c00-120">P</span><span class="sxs-lookup"><span data-stu-id="39c00-120">P</span></span>|<span data-ttu-id="39c00-121">propriedade: `Property` (incluindo propriedades padrão)</span><span class="sxs-lookup"><span data-stu-id="39c00-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="39c00-122">M</span><span class="sxs-lookup"><span data-stu-id="39c00-122">M</span></span>|<span data-ttu-id="39c00-123">método: `Sub`, `Function`, `Declare`, `Operator`</span><span class="sxs-lookup"><span data-stu-id="39c00-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="39c00-124">E</span><span class="sxs-lookup"><span data-stu-id="39c00-124">E</span></span>|<span data-ttu-id="39c00-125">Evento: `Event`</span><span class="sxs-lookup"><span data-stu-id="39c00-125">event: `Event`</span></span>|  
|<span data-ttu-id="39c00-126">!</span><span class="sxs-lookup"><span data-stu-id="39c00-126">!</span></span>|<span data-ttu-id="39c00-127">cadeia de caracteres de erro</span><span class="sxs-lookup"><span data-stu-id="39c00-127">error string</span></span><br /><br /> <span data-ttu-id="39c00-128">O restante da cadeia de caracteres fornece informações sobre o erro.</span><span class="sxs-lookup"><span data-stu-id="39c00-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="39c00-129">O compilador do Visual Basic gera informações de erro para links que não podem ser resolvidos.</span><span class="sxs-lookup"><span data-stu-id="39c00-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="39c00-130">A segunda parte do `String` é o nome totalmente qualificado do item, começando na raiz do namespace.</span><span class="sxs-lookup"><span data-stu-id="39c00-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="39c00-131">O nome do item, seu tipo delimitador (s) e o namespace são separados por pontos.</span><span class="sxs-lookup"><span data-stu-id="39c00-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="39c00-132">Se o nome do próprio item contiver períodos, eles são substituídos pelo sinal numérico (#).</span><span class="sxs-lookup"><span data-stu-id="39c00-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="39c00-133">Presume-se que nenhum item possui um sinal de número diretamente em seu nome.</span><span class="sxs-lookup"><span data-stu-id="39c00-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="39c00-134">Por exemplo, o nome totalmente qualificado do `String` construtor seria `System.String.#ctor`.</span><span class="sxs-lookup"><span data-stu-id="39c00-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="39c00-135">Para propriedades e métodos, se houver argumentos para o método, seguirá a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="39c00-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="39c00-136">Se não houver nenhum argumento, não haverá parênteses.</span><span class="sxs-lookup"><span data-stu-id="39c00-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="39c00-137">Os argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="39c00-137">The arguments are separated by commas.</span></span> <span data-ttu-id="39c00-138">A codificação de cada argumento segue diretamente como ela é codificada em um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assinatura.</span><span class="sxs-lookup"><span data-stu-id="39c00-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39c00-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39c00-139">Example</span></span>  
 <span data-ttu-id="39c00-140">O código a seguir mostra como a ID de cadeias de caracteres para uma classe e seus membros são gerados.</span><span class="sxs-lookup"><span data-stu-id="39c00-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="39c00-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39c00-141">See Also</span></span>  
 [<span data-ttu-id="39c00-142">/doc</span><span class="sxs-lookup"><span data-stu-id="39c00-142">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="39c00-143">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="39c00-143">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
