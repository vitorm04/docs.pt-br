---
description: Parâmetros de método – Referência de C#
title: Parâmetros de método – Referência de C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 7090bf1c3df65cf1e65942404f883b49612e7521
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134400"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="9f71e-103">Parâmetros de método (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9f71e-103">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="9f71e-104">Os parâmetros declarados para um método sem [in](./in-parameter-modifier.md), [ref](./ref.md) nem [out](./out-parameter-modifier.md) são passados para o método chamado pelo valor.</span><span class="sxs-lookup"><span data-stu-id="9f71e-104">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="9f71e-105">Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="9f71e-105">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="9f71e-106">É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="9f71e-106">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="9f71e-107">Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:</span><span class="sxs-lookup"><span data-stu-id="9f71e-107">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="9f71e-108">[params](./params.md) especifica que esse parâmetro pode receber um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="9f71e-108">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="9f71e-109">[in](./in-parameter-modifier.md) especifica que esse parâmetro é passado por referência, mas é lido apenas pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="9f71e-109">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="9f71e-110">[ref](./ref.md) especifica que esse parâmetro é passado por referência e pode ser lido ou gravado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="9f71e-110">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="9f71e-111">[out](./out-parameter-modifier.md) especifica que esse parâmetro é passado por referência e é gravado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="9f71e-111">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9f71e-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="9f71e-112">See also</span></span>

- [<span data-ttu-id="9f71e-113">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="9f71e-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9f71e-114">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="9f71e-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9f71e-115">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="9f71e-115">C# Keywords</span></span>](./index.md)
