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
ms.openlocfilehash: 89b7036215cb7998222e280ceef02073d455a1b2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705932"
---
# <a name="replacing-a-principal-object"></a>Substituindo um objeto Principal
Os aplicativos que fornecem serviços de autenticação devem ser capazes de substituir o objeto **principal** (<xref:System.Security.Principal.IPrincipal>) para um determinado thread. Além disso, o sistema de segurança deve ajudar a proteger a capacidade de substituir os objetos **principais** , pois uma **entidade** de segurança incorreta, comprometida de forma mal-intencionada, compromete o seu aplicativo reivindicando uma identidade ou função inverdadeira. Portanto, os aplicativos que exigem a capacidade de substituir objetos de **entidade de segurança** devem receber o objeto <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> para o controle principal. (Observe que essa permissão não é necessária para executar verificações de segurança baseadas em função ou para a criação de objetos **principal** .)  
  
 O objeto **principal** atual pode ser substituído executando as seguintes tarefas:  
  
1. Crie o objeto **principal** de substituição e o objeto de **identidade** associado.  
  
2. Anexe o novo objeto **principal** ao contexto de chamada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um objeto principal genérico e usá-lo para definir a entidade de segurança de um thread.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
