---
title: Elemento <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 9270552245b3867f0f09741ded3f9da6a8b6c135
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664264"
---
# <a name="nameentry-element"></a>\<Elemento de > nameEntry
Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
\<nameEntry>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**name**|Atributo obrigatório.<br /><br /> Especifica o nome amigável do algoritmo que a classe de criptografia implementa.|  
|**class**|Atributo obrigatório.<br /><br /> Especifica o valor do atributo **Name** no [ \<elemento > cryptoClass](cryptoclass-element.md) .|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.web`|Especifica o elemento raiz para a seção de configuração ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
 O atributo **Name** pode ser o nome de uma das classes abstratas encontradas no <xref:System.Security.Cryptography> namespace. Quando você chama o método **Create** em uma classe de criptografia abstrata, o nome da classe abstrata é passado <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> para o método. CreateFromName retorna uma instância do tipo indicado pelo atributo de **classe** . Se o atributo **Name** for um nome curto, como RSA, você poderá usar esse nome ao chamar o método CreateFromName.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<elemento > nameEntry** para fazer referência a uma classe de criptografia e configurar o tempo de execução. Em seguida, você pode passar a cadeia de caracteres " <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> RSA" para o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método e usar o `MyCryptoRSAClass` método para retornar um objeto.  
  
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

- [Esquema de arquivos de configuração](../index.md)
- [Esquema de configurações de criptografia](index.md)
- [Serviços criptográficos](../../../../../docs/standard/security/cryptographic-services.md)
- [Configurando classes de criptografia](../../configure-cryptography-classes.md)
