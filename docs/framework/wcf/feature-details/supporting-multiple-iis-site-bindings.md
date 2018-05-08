---
title: Suporte a ligações de site do IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 9b92243bb7aaea5c8ecf708ce863e6979bc9f17c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="supporting-multiple-iis-site-bindings"></a>Suporte a ligações de site do IIS
Ao hospedar um serviço do Windows Communication Foundation (WCF) em serviços de informações da Internet (IIS) 7.0, você talvez queira fornecer vários endereços de base que usam o mesmo protocolo no mesmo site. Isso permite que o mesmo serviço responder a um número de URIs diferentes. Isso é útil quando você deseja hospedar um serviço que escuta em http://www.contoso.com e http://contoso.com. Também é útil criar um serviço que tem um endereço base para usuários internos e um endereço base separado para usuários externos. Por exemplo: http://internal.contoso.com e http://www.contoso.com.  
  
> [!NOTE]
>  Essa funcionalidade só está disponível usando o protocolo HTTP.  
  
## <a name="multiple-base-addresses"></a>Vários endereços de Base  
 Este recurso só está disponível para os serviços WCF hospedados no IIS. Este recurso não está habilitado por padrão. Para habilitá-lo, você deve adicionar o `multipleSiteBindingsEnabled` de atributo para o <`serviceHostingEnvironment`> elemento no Web. config arquivo e defina-a como `true`, conforme mostrado no exemplo a seguir.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Ao hospedar um serviço WCF no IIS, o IIS cria um endereço base com base no URI para o diretório virtual que contém o aplicativo. Você pode adicionar endereços de base adicionais que usam o mesmo protocolo usando o Gerenciador de serviços de informações da Internet para adicionar um ou mais associações para seu site da Web. Para cada associação especifica um protocolo (HTTP ou HTTPS), um endereço IP, uma porta e um nome de host. Para obter mais informações sobre como usar o Gerenciador de serviços de informações da Internet, consulte [Gerenciador do IIS (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). Para obter mais informações sobre como adicionar associações a um site, consulte [criar um Site da Web (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Especificar vários endereços de base para o mesmo site afeta o conteúdo da página Ajuda do WCF, importando o esquema e as informações de MEX/WSDL gerado pelo serviço. A página de Ajuda do WCF exibe a linha de comando a ser usado para gerar um cliente WCF que pode se comunicar com o serviço. Esta linha de comando contém apenas o primeiro endereço especificado na associação de IIS para o site da Web. Da mesma forma quando importar o esquema, somente o endereço de base da primeira especificado na associação de IIS é usado. Dados WSDL e MEX conter todos os endereços de base especificados nas associações de IIS.  
  
> [!WARNING]
>  Isso significa que, se um serviço tem dois endereços de base, um para usuários internos e um para usuários externos, ambos são especificados nas informações de MEX/WSDL geradas pelo serviço.
