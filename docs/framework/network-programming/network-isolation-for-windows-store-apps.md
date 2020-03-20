---
title: Isolamento de rede para Aplicativos da Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 390a0281f03b08322cc1bee469b601fd5a1547c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802169"
---
# <a name="network-isolation-for-windows-store-apps"></a>Isolamento de rede para Aplicativos da Windows Store

Classes nos <xref:System.Net> <xref:System.Net.Http>espaços <xref:System.Net.Http.Headers> de nome e nomes podem ser usados para desenvolver aplicativos do Windows Store ou aplicativos de desktop. Quando usado em um aplicativo da Windows Store, as classes nesses namespaces são afetadas pelo isolamento da rede, parte do modelo de segurança do aplicativo usado pelo Windows 8. Para que o sistema permita o acesso à rede, os recursos de rede apropriados deverão ser habilitados no manifesto do aplicativo para um aplicativo da Windows Store.  
  
## <a name="checklist-for-network-isolation"></a>Lista de verificação para isolamento de rede  

Use esta lista de verificação para verificar se o isolamento de rede está configurado para o aplicativo da Windows Store.  
  
1. Determine a direção das solicitações de acesso de rede necessárias para o aplicativo. Isso pode ser solicitações de saída iniciadas pelo cliente ou solicitações de entrada não solicitadas ou pode ser ainda uma combinação de ambos esses tipos de solicitação de rede.  
  
2. Determine o tipo de recursos de rede com os quais o aplicativo se comunicará. Um aplicativo pode precisar se comunicar com recursos confiáveis em uma rede doméstica ou corporativa. Um aplicativo pode precisar se comunicar com recursos na Internet. Um aplicativo pode precisar de acesso a ambos os tipos de recursos de rede.  
  
3. Configure as funcionalidades de isolamento de rede mínimas necessárias no manifesto do aplicativo.  
  
4. Implante e execute seu aplicativo para testá-lo usando as ferramentas de isolamento de rede fornecidas para solução de problemas.  
  
Para obter informações mais detalhadas sobre como configurar os recursos de rede e as ferramentas de isolamento usadas para solucionar [problemas](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) de isolamento da rede, consulte Como configurar os recursos de isolamento de rede na documentação do desenvolvedor do Windows 8.x Store.
  
## <a name="see-also"></a>Confira também

- [Conectando-se a um serviço Web](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Diretrizes e lista de verificação para isolamento de rede](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Início Rápido: Conectando-se usando HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [Como usar manipuladores HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [Como proteger conexões HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [Amostra de HttpClient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
