---
title: "Como criar exceções definidas pelo usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c55489a4c0b86142fcda99c5962c896b73691cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-user-defined-exceptions"></a>Como criar exceções definidas pelo usuário

O .NET fornece uma hierarquia de classes de exceção derivada, em última análise, da classe base <xref:System.Exception>. No entanto, se nenhuma das exceções predefinidas atender às suas necessidades, será possível criar suas próprias classes de exceção derivando da classe <xref:System.Exception>.

Ao criar suas próprias exceções, encerre o nome de classe de exceção definida pelo usuário com a palavra "Exception" e implemente os três construtores comuns, como mostrado no exemplo a seguir. O exemplo define uma nova classe de exceção chamada `EmployeeListNotFoundException`. A classe é derivada de <xref:System.Exception> e inclui três construtores.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Em situações nas quais você está usando a comunicação remota, você deve garantir que os metadados para todas as exceções definidas pelo usuário estejam disponíveis no servidor (computador chamado) e para o cliente (o objeto de proxy ou chamador). Para obter mais informações, consulte [Práticas recomendadas para exceções](best-practices-for-exceptions.md).

## <a name="see-also"></a>Consulte também  
[Exceções](index.md)
