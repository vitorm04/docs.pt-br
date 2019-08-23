---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b3b4cf0d7c2748079af7a94534622b1dbadd3ab5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941885"
---
# <a name="chunkedcookiehandler"></a>\<chunkedCookieHandler>
Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Esse elemento só poderá estar presente se o `mode` atributo `<cookieHandler>` do elemento for "padrão" ou "em bloco".  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<> cookieHandler  
\<chunkedCookieHandler>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|chunkSize|O tamanho máximo, em caracteres, dos dados do cookie HTTP para qualquer cookie HTTP. Você deve ter cuidado ao ajustar o tamanho da parte. Os navegadores da Web têm limites diferentes no tamanho dos cookies e do número permitido por domínio. Por exemplo, a especificação original do Netscape estipulava esses limites: 300 total de cookies, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor de cookie) e 20 cookies por domínio. O padrão é 2000. Necessário.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> cookieHandler](cookiehandler.md)|Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) usa para ler e gravar cookies.|  
  
## <a name="remarks"></a>Comentários  
 Ao especificar um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo do `<cookieHandler>` elemento como "padrão" ou "em bloco", você pode especificar o tamanho da parte que o manipulador de cookies usa para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e definindo seu `chunkSize` atributo. Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho de bloco padrão de 2000 bytes será usado. Este elemento não pode ser especificado quando `mode` o atributo está definido como "Custom".  
  
 O `<chunkedCookieHandler>` elemento é representado <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> pela classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir configura um manipulador de cookie em bloco que grava cookies em partes de 3000 bytes.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
