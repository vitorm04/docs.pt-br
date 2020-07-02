---
title: Exemplos de invocação de plataforma
description: Consulte um exemplo de invocação de plataforma que demonstra como definir e chamar a função MessageBox no User32.dll.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: 97b0720b8954bc24a4058e6a03c32d32bd9e3180
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620801"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="2f1cf-103">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="2f1cf-103">Platform Invoke Examples</span></span>
<span data-ttu-id="2f1cf-104">Os exemplos a seguir demonstram como definir e chamar a função **MessageBox** na User32.dll, passando uma cadeia de caracteres simples como um argumento.</span><span class="sxs-lookup"><span data-stu-id="2f1cf-104">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="2f1cf-105">Nos exemplos, o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> é definido como **Auto** para permitir que a plataforma de destino determine a largura de caractere e o marshaling da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2f1cf-105">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="2f1cf-106">Para obter exemplos adicionais, consulte [Marshaling de dados com invocação de plataforma](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="2f1cf-106">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1cf-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f1cf-107">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="2f1cf-108">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="2f1cf-108">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="2f1cf-109">Especificando um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="2f1cf-109">Specifying a Character Set</span></span>](specifying-a-character-set.md)
