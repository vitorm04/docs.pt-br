---
title: Tipos de dados diversos
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 45b44abc24b968f19b456cbe0be0f25efc8f0ce8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095454"
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="96952-102">Tipos de dados diversos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96952-102">Miscellaneous Data Types (Visual Basic)</span></span>

<span data-ttu-id="96952-103">O Visual Basic fornece vários tipos de dados que não são orientados para números ou caracteres.</span><span class="sxs-lookup"><span data-stu-id="96952-103">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="96952-104">Em vez disso, eles lidam com dados especializados, como valores Sim/Não, valores de data/hora e endereços de objeto.</span><span class="sxs-lookup"><span data-stu-id="96952-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="96952-105">Para uma tabela que mostra uma comparação lado a lado do Visual Basic tipos de dados, consulte [tipos de dados](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="96952-105">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="96952-106">Tipo booliano</span><span class="sxs-lookup"><span data-stu-id="96952-106">Boolean Type</span></span>  

 <span data-ttu-id="96952-107">O [tipo de dados booliano](../../../language-reference/data-types/boolean-data-type.md) é um valor não assinado que é interpretado como `True` ou `False` .</span><span class="sxs-lookup"><span data-stu-id="96952-107">The [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="96952-108">Sua largura de dados depende da plataforma de implementação.</span><span class="sxs-lookup"><span data-stu-id="96952-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="96952-109">Se uma variável puder conter apenas valores de dois Estados, como true/false, yes/no ou on/off, declare-a como `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="96952-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="96952-110">Tipo de data</span><span class="sxs-lookup"><span data-stu-id="96952-110">Date Type</span></span>  

 <span data-ttu-id="96952-111">O [tipo de dados Date](../../../language-reference/data-types/date-data-type.md) é um valor de 64 bits que contém as informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="96952-111">The [Date Data Type](../../../language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="96952-112">Cada incremento representa 100 nanossegundos de tempo decorrido desde o início (12:00 AM) de 1º de Janeiro do ano 1 no calendário gregoriano.</span><span class="sxs-lookup"><span data-stu-id="96952-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="96952-113">Se uma variável puder conter um valor de data, um valor de hora ou ambos, declare-a como `Date` .</span><span class="sxs-lookup"><span data-stu-id="96952-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="96952-114">Tipo de objeto</span><span class="sxs-lookup"><span data-stu-id="96952-114">Object Type</span></span>  

 <span data-ttu-id="96952-115">O [tipo de dados Object](../../../language-reference/data-types/object-data-type.md) é um endereço de 32 bits que aponta para uma instância de objeto dentro de seu aplicativo ou em algum outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96952-115">The [Object Data Type](../../../language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="96952-116">Uma `Object` variável pode se referir a qualquer objeto que seu aplicativo reconhece ou a dados de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="96952-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="96952-117">Isso inclui os dois *tipos de valor*, como `Integer` , `Boolean` e instâncias de estrutura, e *tipos de referência*, que são instâncias de objetos criados a partir de classes como e e instâncias de `String` <xref:System.Windows.Forms.Form> matriz.</span><span class="sxs-lookup"><span data-stu-id="96952-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="96952-118">Se uma variável armazena um ponteiro para uma instância de uma classe que você não conhece no momento da compilação, ou se ele pode apontar para dados de vários tipos de dados, declare-o como `Object` .</span><span class="sxs-lookup"><span data-stu-id="96952-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="96952-119">A vantagem do `Object` tipo de dados é que você pode usá-lo para armazenar dados de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="96952-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="96952-120">A desvantagem é que você incorre em operações extras que levam mais tempo de execução e tornam seu aplicativo mais lento.</span><span class="sxs-lookup"><span data-stu-id="96952-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="96952-121">Se você usar uma `Object` variável para tipos de valor, você incorrerá em *Boxing* e *unboxing*.</span><span class="sxs-lookup"><span data-stu-id="96952-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="96952-122">Se você usá-lo para tipos de referência, você incorrerá em *associação tardia*.</span><span class="sxs-lookup"><span data-stu-id="96952-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96952-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="96952-123">See also</span></span>

- [<span data-ttu-id="96952-124">Caracteres de tipo</span><span class="sxs-lookup"><span data-stu-id="96952-124">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="96952-125">Tipos de dados elementares</span><span class="sxs-lookup"><span data-stu-id="96952-125">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="96952-126">Tipos de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="96952-126">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="96952-127">Tipos de dados de caractere</span><span class="sxs-lookup"><span data-stu-id="96952-127">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="96952-128">Solução de problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="96952-128">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="96952-129">Associação antecipada e tardia</span><span class="sxs-lookup"><span data-stu-id="96952-129">Early and Late Binding</span></span>](../early-late-binding/index.md)
