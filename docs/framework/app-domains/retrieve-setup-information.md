---
title: Recuperando informações de instalação de um domínio de aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 719ea15de135d8bbeb7bb88ea3d5b5874e30b5d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053097"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Recuperando informações de instalação de um domínio de aplicativo
Cada instância de um domínio do aplicativo consiste em propriedades e informações de <xref:System.AppDomainSetup>. Você pode recuperar as informações de configuração de um domínio de aplicativo usando a classe <xref:System.AppDomain?displayProperty=nameWithType>. Essa classe fornece vários membros que recuperam informações de configuração sobre um domínio do aplicativo.  
  
 Você também pode consultar o objeto **AppDomainSetup** do domínio do aplicativo para obter informações de instalação que foram passadas ao domínio quando ele foi criado.  
  
 O exemplo a seguir cria um novo domínio do aplicativo e imprime vários valores no console.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 O exemplo a seguir define e, em seguida, recupera as informações de instalação para um domínio do aplicativo. Observe que `AppDomain.SetupInformation.ApplicationBase` obtém as informações de configuração.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Programação com domínios do aplicativo](application-domains.md#programming-with-application-domains)
- [Usar domínios do aplicativo](use.md)
