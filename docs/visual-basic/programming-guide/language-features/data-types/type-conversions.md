---
title: Conversões de tipo no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1487d98f37e7ef00982de365d0d164435f84567
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="c8172-102">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8172-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="c8172-103">O processo de alteração de um valor de um tipo de dados para outro tipo é chamado *conversão*.</span><span class="sxs-lookup"><span data-stu-id="c8172-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="c8172-104">Conversões são *widening* ou *narrowing*, dependendo das capacidades de dados dos tipos envolvidos.</span><span class="sxs-lookup"><span data-stu-id="c8172-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="c8172-105">Eles também são *implícita* ou *explícita*, dependendo da sintaxe no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c8172-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8172-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c8172-106">In This Section</span></span>  
 [<span data-ttu-id="c8172-107">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="c8172-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="c8172-108">Explica as conversões classificadas por se o tipo de destino pode manter os dados.</span><span class="sxs-lookup"><span data-stu-id="c8172-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="c8172-109">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="c8172-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="c8172-110">Descreve as conversões classificadas por se Visual Basic executa-los automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c8172-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="c8172-111">Conversões entre Cadeias de Caracteres e Outros Tipos</span><span class="sxs-lookup"><span data-stu-id="c8172-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="c8172-112">Ilustra a conversão entre cadeias de caracteres e numéricos, `Boolean`, ou valores de data/hora.</span><span class="sxs-lookup"><span data-stu-id="c8172-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="c8172-113">Como: converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8172-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="c8172-114">Mostra como converter um `Object` variável para qualquer outro tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="c8172-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="c8172-115">Conversões de Matriz</span><span class="sxs-lookup"><span data-stu-id="c8172-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="c8172-116">Orienta o processo de conversão entre matrizes de tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="c8172-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8172-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c8172-117">Related Sections</span></span>  
 [<span data-ttu-id="c8172-118">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="c8172-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="c8172-119">Apresenta os tipos de dados do Visual Basic e descreve como usá-los.</span><span class="sxs-lookup"><span data-stu-id="c8172-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="c8172-120">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="c8172-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="c8172-121">Lista os tipos de dados elementares fornecidos pelo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8172-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="c8172-122">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="c8172-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="c8172-123">Aborda alguns problemas comuns que podem surgir ao trabalhar com tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="c8172-123">Discusses some common problems that can arise when working with data types.</span></span>
