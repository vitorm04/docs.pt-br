---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153029"
---
# <a name="baseaddressprefixfilters"></a>\<baseAddressPrefixFiltros>
Representa uma coleção de elementos de configuração que especificam passar por filtros, que fornecem um mecanismo para escolher as vinculações apropriadas do IIS (Internet Information Services, serviços de informação da Internet) ao hospedar o aplicativo Da Windows Communication Foundation (WCF) no IIS.  
  
> [!WARNING]
> \<baseAddressPrefixFilters> não reconhece "localhost"; use o nome da máquina totalmente qualificado.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçoHospedagemdeambiente>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFiltros>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<adicionar>](add-of-baseaddressprefixfilter.md)|Adiciona um elemento de configuração que especifica um filtro de prefixo para os endereços base usados pelo host de serviço.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviçoHospedagemdeambiente>](servicehostingenvironment.md)|Define o tipo que o ambiente de hospedagem de serviços instancia para um determinado transporte.|  
  
## <a name="remarks"></a>Comentários  
 Um filtro de prefixo fornece uma maneira para os provedores de hospedagem compartilhada especificarem quais URIs devem ser usadas pelo serviço. Ele permite que hosts compartilhados hospedem vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.  
  
 Os sites iIS são contêineres para aplicativos virtuais que contêm diretórios virtuais. O aplicativo em um site pode ser acessado através de uma ou mais vinculações iIS. As ligações iIS fornecem duas informações: protocolo de vinculação e informações vinculativas. O protocolo de vinculação (por exemplo, HTTP) define o esquema sobre o qual ocorre a comunicação e as informações vinculativas (por exemplo, endereço IP, porta, hostheader) contém dados usados para acessar o site.  
  
 O IIS suporta especificar várias vinculações iis para cada site, o que resulta em vários endereços base para cada esquema. Como um serviço WCF hospedado em um site permite vincular a apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado. Os endereços base de entrada, fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.  
  
 Por exemplo, seu site pode conter os seguintes endereços base:
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Você pode usar o seguinte arquivo de configuração para especificar um filtro de prefixo no nível de domínio de aplicativo.  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 Neste exemplo, `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` e são os únicos endereços básicos para seus respectivos esquemas, que podem ser passados.  
  
 Por padrão, quando o prefixo não é especificado, todos os endereços são passados. Especificar o prefixo só permite que o endereço base correspondente para esse esquema seja passado.  
  
> [!NOTE]
> O filtro não suporta curingas. Além disso, os endereços base fornecidos pelo IIS podem `baseAddressPrefixFilters` ter endereços vinculados a outros esquemas não presentes na lista. Esses endereços não são filtrados.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hospedagem](../../../wcf/feature-details/hosting.md)
