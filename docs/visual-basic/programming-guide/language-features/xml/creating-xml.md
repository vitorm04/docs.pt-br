---
title: Criar XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 1c720bc2aca4cec3dd10656d924cf2413fc18a2d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351730"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="0f3ca-102">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f3ca-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="0f3ca-103">Visual Basic permite que você use *literais XML* diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="0f3ca-104">A sintaxe XML literal representa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos e é semelhante à sintaxe XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="0f3ca-105">Isso facilita a criação de elementos XML, documentos e fragmentos programaticamente porque seu código tem a mesma estrutura que o XML final.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f3ca-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0f3ca-106">In This Section</span></span>  
  
|<span data-ttu-id="0f3ca-107">Termo</span><span class="sxs-lookup"><span data-stu-id="0f3ca-107">Term</span></span>|<span data-ttu-id="0f3ca-108">Definição</span><span class="sxs-lookup"><span data-stu-id="0f3ca-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="0f3ca-109">Visão Geral dos Literais XML</span><span class="sxs-lookup"><span data-stu-id="0f3ca-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="0f3ca-110">Introdução a literais XML e como eles se relacionam a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f3ca-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="0f3ca-111">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="0f3ca-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="0f3ca-112">Descreve como usar expressões inseridas em literais XML.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="0f3ca-113">Como criar literais XML</span><span class="sxs-lookup"><span data-stu-id="0f3ca-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="0f3ca-114">Descreve como criar um elemento XML no código usando um literal XML.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="0f3ca-115">Espaço em Branco em Literais XML</span><span class="sxs-lookup"><span data-stu-id="0f3ca-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="0f3ca-116">Descreve como Visual Basic trata o espaço em branco em literais XML.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="0f3ca-117">Especificação dos Literais XML e do XML 1.0</span><span class="sxs-lookup"><span data-stu-id="0f3ca-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="0f3ca-118">Descreve como a sintaxe XML literal no Visual Basic está relacionada à especificação XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="0f3ca-119">Como inserir expressões em literais XML</span><span class="sxs-lookup"><span data-stu-id="0f3ca-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="0f3ca-120">Descreve como usar expressões inseridas em literais XML para criar conteúdo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="0f3ca-121">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="0f3ca-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="0f3ca-122">Descreve as diretrizes para nomear elementos XML e atributos.</span><span class="sxs-lookup"><span data-stu-id="0f3ca-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f3ca-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f3ca-123">See also</span></span>

- [<span data-ttu-id="0f3ca-124">XML</span><span class="sxs-lookup"><span data-stu-id="0f3ca-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
