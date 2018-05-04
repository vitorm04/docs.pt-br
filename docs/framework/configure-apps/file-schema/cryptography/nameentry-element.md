---
title: '&lt;nameEntry&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1bffb72e7c68d10e2c0edd5ec3cb9bcff10cbc0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnameentrygt-element"></a>&lt;nameEntry&gt; elemento
Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<cryptoNameMapping >  
\<nameEntry >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**name**|Atributo obrigatório.<br /><br /> Especifica o nome amigável do algoritmo que implementa a classe de criptografia.|  
|**class**|Atributo obrigatório.<br /><br /> Especifica o valor para o **nome** atributo o [ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elemento.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.web`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
 O **nome** atributo pode ser o nome de uma das classes abstratas encontradas no <xref:System.Security.Cryptography> namespace. Quando você chama o **criar** método em uma classe abstrata de criptografia, o nome de classe abstrata é passado para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> método. **CreateFromName** retorna uma instância do tipo indicado pelo **classe** atributo. Se o **nome** atributo é um nome curto, como RSA, você pode usar esse nome ao chamar o **CreateFromName** método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<nameEntry >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução. Você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Esquema de configurações de criptografia](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Serviços criptográficos](../../../../../docs/standard/security/cryptographic-services.md)  
 [Configurando classes de criptografia](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
