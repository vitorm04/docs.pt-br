---
title: Isolamento de rede para Aplicativos da Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 0d08b09f4ed0314d4f235f10b69bbf1343935841
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333256"
---
# <a name="network-isolation-for-windows-store-apps"></a>Isolamento de rede para Aplicativos da Windows Store
As classes nos namespaces <xref:System.Net>, <xref:System.Net.Http> e <xref:System.Net.Http.Headers> podem ser usadas para desenvolver Aplicativos da Windows Store ou aplic. da área de trabalho. Quando usadas em um aplicativo da Windows Store, as classes nesses namespaces são afetadas pelo isolamento de rede, parte do modelo de segurança do aplicativo usado pelo [!INCLUDE[win8](../../../includes/win8-md.md)]. Para que o sistema permita o acesso à rede, os recursos de rede apropriados deverão ser habilitados no manifesto do aplicativo para um aplicativo da Windows Store.  
  
## <a name="checklist-for-network-isolation"></a>Lista de verificação para isolamento de rede  
 Use esta lista de verificação para verificar se o isolamento de rede está configurado para o aplicativo da Windows Store.  
  
1. Determine a direção das solicitações de acesso de rede necessárias para o aplicativo. Isso pode ser solicitações de saída iniciadas pelo cliente ou solicitações de entrada não solicitadas ou pode ser ainda uma combinação de ambos esses tipos de solicitação de rede.  
  
2. Determine o tipo de recursos de rede com os quais o aplicativo se comunicará. Um aplicativo pode precisar se comunicar com recursos confiáveis em uma rede doméstica ou corporativa. Um aplicativo pode precisar se comunicar com recursos na Internet. Um aplicativo pode precisar de acesso a ambos os tipos de recursos de rede.  
  
3. Configure as funcionalidades de isolamento de rede mínimas necessárias no manifesto do aplicativo.  
  
4. Implante e execute seu aplicativo para testá-lo usando as ferramentas de isolamento de rede fornecidas para solução de problemas.  
  
 Para obter informações mais detalhadas sobre como configurar funcionalidades de rede e as ferramentas de isolamento usadas para solucionar problemas de isolamento de rede, consulte [Como configurar funcionalidades de isolamento de rede](https://go.microsoft.com/fwlink/?LinkID=228265) na documentação do desenvolvedor de [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Consulte também

- [Conectando-se a um serviço Web](https://go.microsoft.com/fwlink/?LinkID=245696)
- [Diretrizes e lista de verificação para isolamento de rede](https://go.microsoft.com/fwlink/?LinkID=228265)
- [Início Rápido: Conectando-se usando HttpClient](https://go.microsoft.com/fwlink/?LinkId=245697)
- [Como usar manipuladores HttpClient](https://go.microsoft.com/fwlink/?LinkId=245699)
- [Como proteger conexões HttpClient](https://go.microsoft.com/fwlink/?LinkId=245698)
- [Amostra de HttpClient](https://go.microsoft.com/fwlink/?LinkId=242550)
