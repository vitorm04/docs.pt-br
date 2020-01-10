---
title: Parâmetros de método – Referência de C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713384"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="dcf06-102">Parâmetros de método (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dcf06-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="dcf06-103">Os parâmetros declarados para um método sem [in](./in-parameter-modifier.md), [ref](./ref.md) nem [out](./out-parameter-modifier.md) são passados para o método chamado pelo valor.</span><span class="sxs-lookup"><span data-stu-id="dcf06-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="dcf06-104">Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="dcf06-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="dcf06-105">É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="dcf06-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="dcf06-106">Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:</span><span class="sxs-lookup"><span data-stu-id="dcf06-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="dcf06-107">[params](./params.md) especifica que esse parâmetro pode receber um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="dcf06-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="dcf06-108">[in](./in-parameter-modifier.md) especifica que esse parâmetro é passado por referência, mas é lido apenas pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="dcf06-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="dcf06-109">[ref](./ref.md) especifica que esse parâmetro é passado por referência e pode ser lido ou gravado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="dcf06-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="dcf06-110">[out](./out-parameter-modifier.md) especifica que esse parâmetro é passado por referência e é gravado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="dcf06-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dcf06-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="dcf06-111">See also</span></span>

- [<span data-ttu-id="dcf06-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="dcf06-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dcf06-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dcf06-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dcf06-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="dcf06-114">C# Keywords</span></span>](./index.md)
