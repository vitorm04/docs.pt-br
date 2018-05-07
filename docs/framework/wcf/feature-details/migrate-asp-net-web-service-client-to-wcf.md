---
title: Como migrar o código de cliente de serviço Web do ASP.NET para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>Como migrar o código de cliente de serviço Web do ASP.NET para o Windows Communication Foundation
O procedimento a seguir descreve as etapas gerais que devem ser seguidas para migrar o código de cliente de serviço Web ASP.NET para o WCF.  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>Para migrar o código de cliente de serviço Web ASP.NET para o WCF  
  
1.  Certifique-se de que um abrangente conjunto de testes existem para o cliente.  
  
2.  Use o Visual Studio 2005 para atualizar o aplicativo cliente .NET 2.0. Execute o conjunto de testes.  
  
3.  Remova o código de cliente do ASP.NET do projeto cliente. Esse código é gerado usando a ferramenta WSDL.exe de módulos.  
  
4.  Gerar código de cliente WCF usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Adicione esse código ao projeto de cliente e mesclar a saída de configuração no arquivo de configuração existente do cliente.  
  
5.  Compile o aplicativo. Repare os erros de compilação, substituindo as referências aos tipos de cliente antigos do ASP.NET com referências para os novos tipos de cliente do WCF.  
  
6.  Execute o conjunto de testes.  
  
## <a name="see-also"></a>Consulte também  
 [Como migrar o código de serviço Web do ASP.NET para o Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
