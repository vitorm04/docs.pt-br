---
title: '&lt;bypassTrustedAppStrongNames&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6988be28e3129748ee7f7996a66c728ccde3c70b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypassTrustedAppStrongNames&gt; elemento
Especifica se deve ignorar a validação de nomes fortes em assemblies de confiança total que são carregados em uma confiança total <xref:System.AppDomain>.  
  
 \<configuration>  
\<runtime>  
\<bypassTrustedAppStrongNames >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o recurso de desvio que evita a validação de nomes fortes para assemblies de confiança total está habilitado. Quando esse recurso está habilitado, nomes fortes não são validados exatidão quando o assembly é carregado. O padrão é `true`.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`true`|Assinaturas de nome forte em assemblies de confiança total não são validadas quando os assemblies são carregados em uma confiança total <xref:System.AppDomain>. Esse é o padrão.|  
|`false`|Assinaturas de nome forte em assemblies de confiança total são validadas quando os assemblies são carregados em uma confiança total <xref:System.AppDomain>. A assinatura de nome forte é verificada apenas para correção de assinatura; ele não é comparado com outro nome de alta segurança para uma correspondência.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 O recurso de desvio de nome forte evita a sobrecarga de verificação de assinatura de nome forte de assemblies de confiança total.  
  
 O recurso de desvio se aplica a qualquer assembly que está assinado com um nome forte e que tem as seguintes características:  
  
-   Totalmente confiável sem o <xref:System.Security.Policy.StrongName> evidência (por exemplo, tem `MyComputer` evidência de zona).  
  
-   Carregado em um <xref:System.AppDomain> totalmente confiável.  
  
-   Carregado de um local sob a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> desse <xref:System.AppDomain>.  
  
-   Não assinado com atraso.  
  
> [!NOTE]
>  Se o recurso de desvio foi desativado para todos os aplicativos no computador usando uma chave do registro, essa configuração do arquivo de configuração não terá efeito. Para obter mais informações, consulte [como: desabilitar o recurso de desvio de nome forte](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar o comportamento que valida a assinatura de nome forte em assemblies de confiança total.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Como desabilitar o recurso de desvio de nome forte](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
