---
title: Cenários de implantação com suporte – WCF
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 2da55176cbfe618b332f2df210e3e1c0516b17ae
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170047"
---
# <a name="supported-deployment-scenarios"></a>Cenários de implantação com suporte

O subconjunto de recursos do Windows Communication Foundation (WCF) tem suportada para uso em aplicativos parcialmente confiáveis foi projetado para atender aos requisitos de algumas, mas nem todos os cenários para uso do WCF. No servidor, o WCF atende aos requisitos de conjunto de provedores de hospedagem compartilhada, que executam aplicativos de terceiros no ASP.NET 2.0 Medium Trust permissão por motivos de segurança de escala de Internet. No cliente, o suporte de confiança parcial do WCF foi projetado para atender aos requisitos de tecnologias de implantação, como [a implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ou tecnologia do aplicativo de navegador XAML do WPF, que permitem a implantação direta e segura de aplicativos da área de trabalho de sites não confiáveis.

## <a name="minimum-permission-requirements"></a>Requisitos de permissão mínimos

O WCF oferece suporte a um subconjunto de recursos em aplicativos em execução em qualquer um dos seguintes conjuntos de permissões nomeadas padrão:

- Permissões de confiança médio

- Permissões da zona da Internet

A tentativa de usar o WCF em aplicativos parcialmente confiáveis com permissões mais restritivas pode resultar em exceções de segurança em tempo de execução.

Para obter mais informações sobre os recursos com suporte nesses conjuntos de permissão, consulte [compatibilidade de recursos de confiança parcial](partial-trust-feature-compatibility.md).

## <a name="partial-trust-on-the-server"></a>Confiança parcial no servidor

Muitos provedores comerciais de serviços de hospedagem de aplicativo Web do ASP.NET exigem que os aplicativos em execução em seus servidores executados no conjunto de permissões de confiança de média do ASP.NET 2.0. Serviços WCF podem ser executados nesses ambientes desde que eles usam o <xref:System.ServiceModel.BasicHttpBinding>, o <xref:System.ServiceModel.WebHttpBinding>, ou o <xref:System.ServiceModel.WSHttpBinding> com segurança em nível de transporte.

Os serviços WCF em execução em ambientes de hospedagem de confiança média também podem atuar como serviços de camada intermediária, enviando mensagens para outros servidores em resposta às solicitações do cliente. Cenários de camada intermediária no servidor têm suporte se o ambiente de hospedagem tiver concedido o aplicativo apropriado <xref:System.Net.WebPermission> para fazer solicitações de saída para o servidor desejado.

Além de mensagens SOAP usando uma das associações SOAP com suporte, o WCF oferece suporte a <xref:System.ServiceModel.WebHttpBinding> para criação de serviços de estilo da Web em aplicativos parcialmente confiáveis. O [modelo de programação do WCF Web HTTP](wcf-web-http-programming-model.md), [Sindicalização do WCF](wcf-syndication.md), e [integração AJAX e suporte para JSON](ajax-integration-and-json-support.md) todos os recursos do WCF têm suporte em confiança parcial.

Serviços de fluxo de trabalho exigem permissões de confiança total e não podem ser usados em aplicativos parcialmente confiáveis.

Para obter mais informações, confira [Como: Usar confiança média no ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=84603).

## <a name="partial-trust-on-the-client"></a>Confiança parcial no cliente

Determinadas precauções de segurança devem ter cuidadas ao baixar e executar código não confiáveis de sites da Internet. Ambos [a implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) e aplicativo de navegador da XAML (XBAP) do WPF tecnologia de tornar o uso de confiança parcial para conceder permissões limitadas (zona da Internet) para código não confiável.

WCF pode ser usado para se comunicar com servidores remotos de dentro de aplicativos parcialmente confiáveis, implantados pelo [a implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ou XBAP. Inclui o conjunto de permissões da zona da Internet <xref:System.Net.WebPermission> para o host de origem, que permite que esses aplicativos se comuniquem com seu servidor de origem usando qualquer uma das associações WCF com suporte descritas no [compatibilidade de recursos de confiança parcial ](partial-trust-feature-compatibility.md).

## <a name="see-also"></a>Consulte também

- [Segurança de acesso do código](../../misc/code-access-security.md)
- [Visão geral de aplicativos hospedados pelo navegador do Windows Presentation Foundation](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [Confiança parcial](partial-trust.md)
- [Níveis de confiança do ASP.NET e arquivos de política](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
