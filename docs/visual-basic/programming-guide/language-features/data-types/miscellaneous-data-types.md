---
title: Tipos de dados diversos (Visual Basic) | Documentos do Microsoft
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
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
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
ms.openlocfilehash: ed7b61a5ec57ff85347f2c257e321ab9ec425274
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="42273-102">Tipos de dados diversos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42273-102">Miscellaneous Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="42273-103">fornece vários tipos de dados que não estão familiarizados com números ou caracteres.</span><span class="sxs-lookup"><span data-stu-id="42273-103"> supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="42273-104">Em vez disso, eles lidam com dados especializados, como Sim/não valores, valores de data/hora e endereços de objeto.</span><span class="sxs-lookup"><span data-stu-id="42273-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="42273-105">Para uma tabela que mostre uma comparação lado a lado do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="42273-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="42273-106">Tipo booleano</span><span class="sxs-lookup"><span data-stu-id="42273-106">Boolean Type</span></span>  
 <span data-ttu-id="42273-107">O [tipo de dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) é um valor sem sinal que é interpretado como `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="42273-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="42273-108">Sua largura de dados depende da plataforma de implementação.</span><span class="sxs-lookup"><span data-stu-id="42273-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="42273-109">Se uma variável pode conter apenas valores de dois estados, como verdadeiro/falso, Sim/não ou ativado/desativado, declare-o como `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="42273-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="42273-110">Tipo de data</span><span class="sxs-lookup"><span data-stu-id="42273-110">Date Type</span></span>  
 <span data-ttu-id="42273-111">O [tipo de dados data](../../../../visual-basic/language-reference/data-types/date-data-type.md) é um valor de 64 bits que contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="42273-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="42273-112">Cada incremento representa 100 nanossegundos de tempo decorrido desde o início (12:00 AM) de 1º de janeiro do ano 1 no calendário gregoriano.</span><span class="sxs-lookup"><span data-stu-id="42273-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="42273-113">Se uma variável pode conter um valor de data, um valor de tempo ou ambos, declare-o como `Date`.</span><span class="sxs-lookup"><span data-stu-id="42273-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="42273-114">Tipo de Objeto</span><span class="sxs-lookup"><span data-stu-id="42273-114">Object Type</span></span>  
 <span data-ttu-id="42273-115">O [tipo de dados de objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md) é um endereço de 32 bits que aponta para uma instância de objeto dentro de seu aplicativo ou em algum outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42273-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="42273-116">Um `Object` variável pode referir-se a qualquer objeto que seu aplicativo reconheça, ou aos dados de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="42273-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="42273-117">Isso inclui tanto *tipos de valor*, como `Integer`, `Boolean`e instâncias de estrutura e *tipos de referência*, que são instâncias de objetos criados a partir de classes, como `String` e <xref:System.Windows.Forms.Form>e instâncias de array.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="42273-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="42273-118">Se uma variável armazena um ponteiro para uma instância de uma classe que você não souber em tempo de compilação, ou se ele pode apontar para dados de vários tipos de dados, declare-o como `Object`.</span><span class="sxs-lookup"><span data-stu-id="42273-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="42273-119">A vantagem do `Object` é do tipo de dados que você pode usá-lo para armazenar dados de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="42273-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="42273-120">A desvantagem é que você provoca operações extras que levam mais tempo de execução e fazer com que seu aplicativo execute mais lentamente.</span><span class="sxs-lookup"><span data-stu-id="42273-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="42273-121">Se você usar um `Object` variável para tipos de valor, você provoca *conversão boxing* e *unboxing*.</span><span class="sxs-lookup"><span data-stu-id="42273-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="42273-122">Se você usá-lo para tipos de referência, você provoca *ligação tardia*.</span><span class="sxs-lookup"><span data-stu-id="42273-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42273-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42273-123">See Also</span></span>  
 <span data-ttu-id="42273-124">[Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="42273-124">[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="42273-125"> [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="42273-125"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="42273-126"> [Tipos de dados numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="42273-126"> [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span></span>  
<span data-ttu-id="42273-127"> [Tipos de dados de caractere](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="42273-127"> [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span></span>  
<span data-ttu-id="42273-128"> [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="42273-128"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="42273-129"> [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="42273-129"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
