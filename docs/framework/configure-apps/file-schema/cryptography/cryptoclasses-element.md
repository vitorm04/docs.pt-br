---
title: Elemento <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155240"
---
# <a name="cryptoclasses-element"></a>\<criptoClasses> Element
Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no [ \<nomeEntry>](nameentry-element.md) elemento.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<criptografiaConfigurações>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de mapeamento de nomes de cripto**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<criptoClasses>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de criptoclasse](cryptoclass-element.md)|Contém uma classe de criptografia que tem um mapeamento para um nome amigável no ** \<nomeEntry>** elemento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`cryptographySettings`|Contém configurações de criptografia.|  
|`cryptoNameMapping`|Contém mapeamentos de classes para nomes amigáveis.|  
|`mscorlib`|Contém `cryptographySettings` o elemento.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ** \<** mostra como usar o elemento cryptoClass>para referenciar uma classe de criptografia e configurar o tempo de execução. Em seguida, você pode passar a <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> string "RSA" para o método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Security.Cryptography>
- [Esquema de arquivo de configuração](../index.md)
- [Esquema de configurações de criptografia](index.md)
- [Serviços criptográficos](../../../../standard/security/cryptographic-services.md)
- [System.Security.Cryptoography.CryptoConfig.CreateFromName](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [Configurando classes de criptografia](../../configure-cryptography-classes.md)
