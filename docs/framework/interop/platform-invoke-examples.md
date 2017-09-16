---
title: "Exemplos de invocação de plataforma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ec8f261ab6f6f8b0c57f302859e1212d237b12aa
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="platform-invoke-examples"></a>Exemplos de invocação de plataforma
Os exemplos a seguir demonstram como definir e chamar a função **MessageBox** na User32.dll, passando uma cadeia de caracteres simples como um argumento. Nos exemplos, o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> é definido como **Auto** para permitir que a plataforma de destino determine a largura de caractere e o marshaling da cadeia de caracteres.  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]   
  
 Para obter exemplos adicionais, consulte [Marshaling de dados com invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [Especificando um conjunto de caracteres](../../../docs/framework/interop/specifying-a-character-set.md)

