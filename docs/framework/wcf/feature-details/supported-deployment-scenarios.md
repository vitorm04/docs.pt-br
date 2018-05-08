---
title: Cenários de desempenho com suporte
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: d0afd12b1c17f9356146aa13c90f8db65ed9ec0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="supported-deployment-scenarios"></a>Cenários de desempenho com suporte
O subconjunto de recursos do Windows Communication Foundation (WCF) tem suportada para uso em aplicativos parcialmente confiáveis foi projetado para atender aos requisitos de algumas, mas nem todos os cenários para usar o WCF. No servidor, o WCF atende os requisitos de escala da Internet compartilhada provedores de hospedagem que executam aplicativos de terceiros no [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] conjunto por motivos de segurança de permissões de confiança média. No cliente, o suporte de confiança parcial do WCF é projetado para atender aos requisitos de tecnologias de implantação, como [implantação de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) ou [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]da tecnologia de aplicativo de navegador XAML, que permitem direta e segura implantação de aplicativos de área de trabalho de sites não confiáveis.  
  
## <a name="minimum-permission-requirements"></a>Requisitos de permissão mínima  
 O WCF dá suporte a um subconjunto de recursos em aplicativos em execução em qualquer um dos seguintes conjuntos de permissões nomeadas padrão:  
  
-   Permissões de confiança médio  
  
-   Permissões de zona da Internet  
  
 Tentativa de usar o WCF em aplicativos parcialmente confiáveis com permissões mais restritivas pode resultar em exceções de segurança em tempo de execução.  
  
 Para obter mais informações sobre os recursos com suporte nesses conjuntos de permissão, consulte [compatibilidade de recurso de relação de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Confiança parcial no servidor  
 Muitos provedores comerciais de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] autorizar que executam aplicativos em execução em seus servidores em de serviços de hospedagem de aplicativos Web a [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] conjunto de permissões de confiança média. Serviços WCF podem ser executados nesses ambientes desde que eles usam o <xref:System.ServiceModel.BasicHttpBinding>, o <xref:System.ServiceModel.WebHttpBinding>, ou <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> com segurança em nível de transporte.  
  
 Serviços WCF em execução em ambientes de hospedagem de confiança média também podem agir como serviços de camada intermediária, enviando mensagens para outros servidores em resposta a solicitações de cliente. Cenários de camada intermediária do servidor têm suporte se o ambiente de hospedagem concedido o aplicativo apropriado <xref:System.Net.WebPermission> para fazer solicitações de saída para o servidor desejado.  
  
 Além de mensagens SOAP usando uma das ligações de SOAP com suporte, o WCF suporta o <xref:System.ServiceModel.WebHttpBinding> para criar serviços de estilo da Web em aplicativos parcialmente confiáveis. O [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), e [integração de AJAX e suporte a JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) todos os recursos do WCF têm suporte em confiança parcial.  
  
 Serviços de fluxo de trabalho exigem permissões de confiança total e não podem ser usados em aplicativos parcialmente confiáveis.  
  
 Para obter mais informações, consulte [como: uso de confiança média no ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>Confiança parcial no cliente  
 Certas precauções de segurança devem ter cuidadas ao baixar e executar código não confiáveis de sites da Internet. Ambos [implantação de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) e [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]XAML navegador XBAP (aplicativos) tecnologia fazer uso de confiança parcial para conceder permissões limitadas (zona da Internet) para código não confiável.  
  
 WCF pode ser usado para se comunicar com servidores remotos a partir parcialmente confiáveis aplicativos implantados pelo [implantação de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) ou XBAP. Inclui o conjunto de permissões da zona da Internet <xref:System.Net.WebPermission> para o host de origem, que permite que esses aplicativos para se comunicar com o servidor de origem usando qualquer uma das associações WCF com suporte, descritas em [compatibilidade de recurso de relação de confiança parcial ](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança de acesso do código](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Visão geral de aplicativos hospedados em navegador do Windows Presentation Foundation](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [Confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [Confiança média do ASP.Net](http://go.microsoft.com/fwlink/?LinkId=69328)
