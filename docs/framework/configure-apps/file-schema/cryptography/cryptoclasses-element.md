---
title: '&lt;cryptoClasses&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2706d2466bd7139d8a6c20802c32dd19f64abb40
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcryptoclassesgt-element"></a>&lt;cryptoClasses&gt; elemento
Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento [ \<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<cryptoNameMapping >  
\<cryptoClasses >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento **\<nameEntry>**.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`cryptographySettings`|Contém configurações de criptografia.|  
|`cryptoNameMapping`|Contém mapeamentos de classes para nomes amigáveis.|  
|`mscorlib`|Contém o `cryptographySettings` elemento.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<cryptoClass >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução. Você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography>  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Esquema de configurações de criptografia](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Serviços criptográficos](../../../../../docs/standard/security/cryptographic-services.md)  
 [System.Security.Cryptography.CryptoConfig.CreateFromName](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)  
 [Configurando classes de criptografia](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
