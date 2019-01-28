---
title: Parâmetros de método – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 72917d356ed0fce96502faeef68494c7fdcb214f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564754"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="d43b2-102">Parâmetros de método (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d43b2-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="d43b2-103">Os parâmetros declarados para um método sem [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nem [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) são passados para o método chamado pelo valor.</span><span class="sxs-lookup"><span data-stu-id="d43b2-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="d43b2-104">Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="d43b2-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="d43b2-105">É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="d43b2-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="d43b2-106">Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:</span><span class="sxs-lookup"><span data-stu-id="d43b2-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="d43b2-107">[params](../../../csharp/language-reference/keywords/params.md) especifica que esse parâmetro pode receber um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="d43b2-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="d43b2-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) especifica que esse parâmetro é passado por referência, mas é lido apenas pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="d43b2-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="d43b2-109">[ref](../../../csharp/language-reference/keywords/ref.md) especifica que esse parâmetro é passado por referência e pode ser lido ou gravado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="d43b2-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="d43b2-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) especifica que esse parâmetro é passado por referência e é gravado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="d43b2-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d43b2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d43b2-111">See also</span></span>

- [<span data-ttu-id="d43b2-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d43b2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d43b2-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d43b2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d43b2-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d43b2-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
