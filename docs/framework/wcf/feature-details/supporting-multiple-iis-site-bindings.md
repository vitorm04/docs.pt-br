---
title: Suporte a ligações de site do IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 5a8b06d86b505452f9ded808f727343b1453e592
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696100"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Suporte a ligações de site do IIS
Ao hospedar um serviço do Windows Communication Foundation (WCF) em serviços de informações da Internet (IIS) 7.0, você talvez queira fornecer vários endereços de base que usam o mesmo protocolo no mesmo site. Isso permite que o mesmo serviço responder a um número de URIs diferentes. Isso é útil quando você deseja hospedar um serviço que escuta `http://www.contoso.com` e `http://contoso.com`. Também é útil criar um serviço que tem um endereço básico para usuários internos e um endereço base separado para usuários externos. Por exemplo: `http://internal.contoso.com` e `http://www.contoso.com`.  
  
> [!NOTE]
>  Essa funcionalidade só está disponível usando o protocolo HTTP.  
  
## <a name="multiple-base-addresses"></a>Vários endereços de Base  
 Esse recurso só está disponível para os serviços WCF que são hospedados no IIS. Este recurso não está habilitado por padrão. Para habilitá-lo, você deve adicionar o `multipleSiteBindingsEnabled` de atributo para o <`serviceHostingEnvironment`> elemento no Web. config arquivo e defina-a como `true`, conforme mostrado no exemplo a seguir.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Ao hospedar um serviço WCF no IIS, o IIS cria um endereço base para você com base no URI para o diretório virtual que contém o aplicativo. Você pode adicionar endereços de base adicionais que usam o mesmo protocolo usando o Gerenciador de serviços de informações da Internet para adicionar uma ou mais associações ao seu site da Web. Para cada associação de especificar um protocolo (HTTP ou HTTPS), um endereço IP, uma porta e um nome de host. Para obter mais informações sobre como usar o Gerenciador de serviços de informações da Internet, consulte [o Gerenciador do IIS (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164057). Para obter mais informações sobre como adicionar associações a um site, consulte [criar um Site da Web (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Especificar vários endereços de base para o mesmo site afeta o conteúdo da página Ajuda do WCF, importação de esquema e as informações de MEX/WSDL gerado pelo serviço. A página de Ajuda do WCF exibe a linha de comando a ser usado para gerar um cliente WCF que pode se comunicar com o serviço. Essa linha de comando contém somente o primeiro endereço especificado na associação de IIS para o site da Web. Da mesma forma quando a importação de esquema, somente o endereço da primeira base especificado na associação do IIS é usado. Dados WSDL e MEX contêm todos os endereços base especificados nas associações de IIS.  
  
> [!WARNING]
>  Isso significa que, se um serviço tem dois endereços de base, um para usuários internos e outro para usuários externos, ambos são especificadas nas informações de MEX/WSDL geradas pelo serviço.
