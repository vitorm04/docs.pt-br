---
title: "Conversões de tipo no Visual Basic | Documentos do Microsoft"
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
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion
- conversions, data type
- changing data types
- data type conversion
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: 13
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
ms.openlocfilehash: 61606572dd1f10dc5df4ed4baec02f230a23c8d6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="738f1-102">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="738f1-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="738f1-103">O processo de alterar um valor de um tipo de dados para outro tipo é chamado *conversão*.</span><span class="sxs-lookup"><span data-stu-id="738f1-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="738f1-104">Conversões são *widening* ou *narrowing*, dependendo das capacidades de dados dos tipos envolvidos.</span><span class="sxs-lookup"><span data-stu-id="738f1-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="738f1-105">Eles também são *implícita* ou *explícita*, dependendo da sintaxe no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="738f1-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="738f1-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="738f1-106">In This Section</span></span>  
 [<span data-ttu-id="738f1-107">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="738f1-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="738f1-108">Explica as conversões classificadas por se o tipo de destino pode manter os dados.</span><span class="sxs-lookup"><span data-stu-id="738f1-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="738f1-109">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="738f1-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="738f1-110">Descreve as conversões classificadas se [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] executa-los automaticamente.</span><span class="sxs-lookup"><span data-stu-id="738f1-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="738f1-111">Conversões entre Cadeias de Caracteres e Outros Tipos</span><span class="sxs-lookup"><span data-stu-id="738f1-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="738f1-112">Ilustra a conversão entre cadeias de caracteres e numéricos, `Boolean`, ou valores de data/hora.</span><span class="sxs-lookup"><span data-stu-id="738f1-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="738f1-113">Como: converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="738f1-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="738f1-114">Mostra como converter um `Object` variável em qualquer outro tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="738f1-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="738f1-115">Conversões de Matriz</span><span class="sxs-lookup"><span data-stu-id="738f1-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="738f1-116">Percorre o processo de conversão entre matrizes de tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="738f1-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="738f1-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="738f1-117">Related Sections</span></span>  
 [<span data-ttu-id="738f1-118">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="738f1-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="738f1-119">Apresenta o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados e descreve como usá-los.</span><span class="sxs-lookup"><span data-stu-id="738f1-119">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="738f1-120">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="738f1-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="738f1-121">Lista os tipos de dados elementares fornecidos pelo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="738f1-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 [<span data-ttu-id="738f1-122">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="738f1-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="738f1-123">Aborda alguns problemas comuns que podem ocorrer ao trabalhar com tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="738f1-123">Discusses some common problems that can arise when working with data types.</span></span>
