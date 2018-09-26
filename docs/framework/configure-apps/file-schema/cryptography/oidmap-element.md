---
title: '&lt;oidMap&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4ec2ba884f0f60182dd59bb6a4491e223f43ce1a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196610"
---
# <a name="ltoidmapgt-element"></a>&lt;oidMap&gt; elemento
Contém mapeamentos OID (identificador) de objeto do ASN.1 para classes.  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<oidMap >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<oidEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|Mapeia um OID do ASN.1 para um nome amigável.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`cryptographySettings`|Contém configurações de criptografia.|  
|`mscorlib`|Contém o `cryptographySettings` elemento.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<oidMap >** elemento para conter um mapeamento de um OID do algoritmo de hash RIPEMD-160 para uma implementação do algoritmo hash.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Esquema de configurações de criptografia](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Serviços criptográficos](../../../../../docs/standard/security/cryptographic-services.md)  
 [Configurando classes de criptografia](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [Mapeando identificadores de objeto para algoritmos de criptografia](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
