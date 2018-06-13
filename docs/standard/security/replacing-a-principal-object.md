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
ms.openlocfilehash: 94391471fecd92aeadec4da39cdd5b6f80bb6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581158"
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
