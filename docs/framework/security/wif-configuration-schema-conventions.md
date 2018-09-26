---
title: Convenções do esquema de configuração do WIF
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: dc2e8f7070af3ef907e4987964bb5aa83f889186
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206433"
---
# <a name="wif-configuration-schema-conventions"></a>Convenções do esquema de configuração do WIF
Este tópico aborda as convenções usadas nos tópicos de configuração do WIF (Windows Identity Foundation) e descreve alguns recursos e atributos comuns usados nas seções [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) e [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Modos  
 Muitos dos elementos de configuração do WIF têm um atributo `mode`. Normalmente, esse atributo controla qual classe é usada para fazer determinada parte do processamento e quais elementos de configuração são permitidos como elementos filho do elemento atual. Um erro de configuração será acionado se elementos que estão incluídos no arquivo de configuração forem ignorados devido às configurações do modo.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Valores do intervalo de tempo  
 Quando <xref:System.TimeSpan> é usado como o tipo de um atributo, consulte o método <xref:System.TimeSpan.Parse%28System.String%29> para ver o formato permitido. Esse formato está em conformidade com a especificação a seguir.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Por exemplo, “30”, “30.00:00” e “30.00:00:00” significam 30 dias, enquanto “00:05”, “00:05:00” e “0.00:05:00.00” significam 5 minutos.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Referências de certificado  
 Vários elementos levam referências a certificados usando o elemento `<certificateReference>`. Ao referenciar um certificado, os atributos a seguir estão disponíveis.  
  
|||  
|-|-|  
|`storeLocation`|Um valor da enumeração <xref:System.Security.Cryptography.X509Certificates.StoreLocation>: `CurrentUser` ou `CurrentMachine`.|  
|`storeName`|Um valor da enumeração <xref:System.Security.Cryptography.X509Certificates.StoreName>; os mais úteis para este contexto são `My` e `TrustedPeople`.|  
|`x509FindType`|Um valor da enumeração <xref:System.Security.Cryptography.X509Certificates.X509FindType>; os mais úteis para este contexto são `FindBySubjectName` e `FindByThumbprint`. Para eliminar a possibilidade de erros, é recomendável que o tipo `FindByThumbprint` seja usado em ambientes de produção.|  
|`findValue`|O valor usado para encontrar o certificado, com base no atributo `x509FindType`. Para eliminar a possibilidade de erros, é recomendável que o tipo `FindByThumbprint` seja usado em ambientes de produção. Quando `FindByThumbPrint` é especificado, esse atributo usa um valor que é o formato de cadeia de caracteres hexadecimal da impressão digital do certificado; por exemplo, “97249e1a5fa6bee5e515b82111ef524a4c91583f”.|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Referências de tipo personalizado  
 Vários elementos referenciam tipos personalizados usando o atributo `type`. Esse atributo deve especificar o nome do tipo personalizado. Para referenciar um tipo do GAC (Cache de Assembly Global), um nome forte deve ser usado. Para referenciar um tipo de um assembly no diretório Bin/, uma referência simples qualificada pelo assembly pode ser usada. Os tipos definidos no diretório App_Code/ também podem ser referenciados apenas especificando o nome do tipo sem nenhum assembly qualificado.  
  
 Os tipos personalizados devem ser derivados do tipo especificado e devem fornecer um construtor `public` padrão (0 argumento).  
  
## <a name="see-also"></a>Consulte também  
 [\<System. IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
