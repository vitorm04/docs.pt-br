---
title: Substituindo um objeto Principal
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
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c53064ae12889df09b5259fbb7c8159cfdcd07aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="replacing-a-principal-object"></a>Substituindo um objeto Principal
Aplicativos que fornecem serviços de autenticação devem ser capazes de substituir o **Principal** objeto (<xref:System.Security.Principal.IPrincipal>) para um determinado thread. Além disso, o sistema de segurança deve ajudar a proteger a capacidade de substituir **Principal** objetos porque um maliciosamente anexado incorreto **Principal** comprometa a segurança do seu aplicativo reivindicar uma verdade identidade ou uma função. Portanto, aplicativos que requerem a capacidade de substituir **Principal** objetos devem ser concedidos a <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objeto de controle principal. (Observe que essa permissão não é necessária para executar verificações de segurança baseada em função ou para a criação de **Principal** objetos.)  
  
 Atual **Principal** objeto pode ser substituído por executar as seguintes tarefas:  
  
1.  Criar a substituição **Principal** do objeto e associados **identidade** objeto.  
  
2.  Anexar o novo **Principal** objeto para o contexto de chamada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um objeto principal genérico e usá-lo para definir a entidade de um thread.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
