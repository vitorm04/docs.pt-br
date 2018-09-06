---
title: Substituindo um objeto Principal
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfcd912fc16aa8d4b89a4f455d65b0294593cead
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886520"
---
# <a name="replacing-a-principal-object"></a>Substituindo um objeto Principal
Aplicativos que fornecem serviços de autenticação devem ser capazes de substituir os **Principal** objeto (<xref:System.Security.Principal.IPrincipal>) para um determinado thread. Além disso, o sistema de segurança deve ajudar a proteger a capacidade de substituir **Principal** objetos porque um maliciosamente anexado incorreto **Principal** comprometa a segurança do seu aplicativo por reivindicar uma identidade irreais ou função. Portanto, aplicativos que exigem a capacidade de substituir **Principal** objetos devem ser concedidos a <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objeto para o controle principal. (Observe que essa permissão não é necessária para realizar verificações de segurança baseada em função ou de criação **Principal** objetos.)  
  
 O atual **Principal** objeto pode ser substituído por meio das seguintes tarefas:  
  
1.  Criar a substituição **Principal** do objeto e associados **identidade** objeto.  
  
2.  Anexar o novo **Principal** objeto para o contexto de chamada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um objeto de entidade genérico e usá-lo para definir a entidade de um thread.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
- [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
