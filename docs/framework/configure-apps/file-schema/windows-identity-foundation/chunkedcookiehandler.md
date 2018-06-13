---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 193b783e44fe4386d3575e180dc5baa6a7f9a8be
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758367"
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Esse elemento só pode estar presente se a `mode` atributo do `<cookieHandler>` elemento é "Padrão" ou "Blocos".  
  
 \<System >  
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
|tamanho máximo permitido|O tamanho máximo, em caracteres, os dados de cookie HTTP para qualquer um cookie HTTP. Você deve ter cuidado ao ajustar o tamanho da parte. Navegadores da Web têm limites diferentes para o tamanho de cookies e o número permitido por domínio. Por exemplo, a especificação de Netscape original estipulado esses limites: total de 300 cookies, 4096 bytes por cabeçalho de cookie (incluindo metadados, não apenas o valor do cookie) e 20 cookies por domínio. O padrão é 2000. Necessário.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) usa para ler e gravar cookies.|  
  
## <a name="remarks"></a>Comentários  
 Quando você especifica um <xref:System.IdentityModel.Services.ChunkedCookieHandler> definindo o `mode` atributo do `<cookieHandler>` elemento "Padrão" ou "Em partes", você pode especificar o tamanho da parte que usa o manipulador de cookie para ler e gravar cookies, incluindo um `<chunkedCookieHandler>` elemento filho e Configurando seu `chunkSize` atributo. Se o `<chunkedCookieHandler>` elemento não estiver presente, o tamanho da parte padrão de bytes 2000 é usado. Esse elemento não pode ser especificado quando o `mode` atributo é definido como "Custom".  
  
 O `<chunkedCookieHandler>` elemento é representado pela <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir configura um manipulador de cookie em partes que grava cookies em blocos de 3000 bytes.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
