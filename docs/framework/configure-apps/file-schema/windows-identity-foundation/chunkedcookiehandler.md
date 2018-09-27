---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: f5592e0fd02d34b2882182196e0aa9425672a8fe
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400810"
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Esse elemento pode estar presente apenas se o `mode` atributo do `<cookieHandler>` elemento é "Default" ou "Em bloco".  
  
 \<IdentityModel >  
\<federationConfiguration >  
\<cookieHandler >  
\<chunkedCookieHandler >  
  
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
|tamanho máximo permitido|O tamanho máximo, em caracteres, dos dados para qualquer cookie HTTP um cookie HTTP. Você deve ter cuidado ao ajustar o tamanho da parte. Navegadores da Web têm diferentes limites no tamanho dos cookies e o número permitido por domínio. Por exemplo, a especificação original do Netscape estipulados esses limites: total de 300 cookies, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor do cookie) e 20 cookies por domínio. O padrão é 2000. Necessário.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configura a <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) usa para ler e gravar cookies.|  
  
## <a name="remarks"></a>Comentários  
 Quando você especifica um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo da `<cookieHandler>` elemento "Padrão" ou "Em bloco", você pode especificar o tamanho da parte que o manipulador de cookie usa para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e definindo seu `chunkSize` atributo. Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho da parte padrão de 2.000 bytes é usado. Esse elemento não pode ser especificado quando o `mode` atributo é definido como "Custom".  
  
 O `<chunkedCookieHandler>` elemento é representado pelo <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir configura um manipulador de cookie em partes que grava os cookies em blocos de 3000 bytes.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
