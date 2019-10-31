---
title: Exemplos de invocação de plataforma
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
ms.openlocfilehash: da157a40819ada3914cf1791c8ca3f7b30e8c837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124752"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="03d19-102">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="03d19-102">Platform Invoke Examples</span></span>
<span data-ttu-id="03d19-103">Os exemplos a seguir demonstram como definir e chamar a função **MessageBox** na User32.dll, passando uma cadeia de caracteres simples como um argumento.</span><span class="sxs-lookup"><span data-stu-id="03d19-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="03d19-104">Nos exemplos, o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> é definido como **Auto** para permitir que a plataforma de destino determine a largura de caractere e o marshaling da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="03d19-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="03d19-105">Para obter exemplos adicionais, consulte [Marshaling de dados com invocação de plataforma](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="03d19-105">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d19-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03d19-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="03d19-107">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="03d19-107">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="03d19-108">Especificando um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="03d19-108">Specifying a Character Set</span></span>](specifying-a-character-set.md)
