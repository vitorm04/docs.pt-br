---
title: '&lt;supportPortability&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a8a454919a195a0f0c03ed6890e51b2723f64fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754100"
---
# <a name="ltsupportportabilitygt-element"></a>&lt;supportPortability&gt; elemento
Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<assemblyBinding > elemento  
\<supportPortability > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|PCT|Atributo obrigatório.<br /><br /> Especifica o token de chave pública do assembly afetado, como uma cadeia de caracteres.|  
|habilitado|Atributo opcional.<br /><br /> Especifica se o suporte para a portabilidade entre implementações de assembly do .NET Framework especificado deve ser habilitado.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Habilite o suporte para a portabilidade entre implementações de assembly do .NET Framework especificado. Esse é o padrão.|  
|false|Desabilite o suporte para a portabilidade entre implementações de assembly do .NET Framework especificado. Isso permite que o aplicativo para que as referências a várias implementações do assembly especificado.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], automaticamente é oferecido suporte para aplicativos que podem usar qualquer uma das duas implementações do .NET Framework, por exemplo uma implementação do .NET Framework ou o .NET Framework para a implementação do Silverlight. As duas implementações de um determinado assembly do .NET Framework são vistas como equivalentes por do fichário de assembly. Em alguns cenários, esse recurso de portabilidade de aplicativo causa problemas. Nesses cenários, o `<supportPortability>` elemento pode ser usado para desabilitar o recurso.  
  
 Um cenário como esse é um assembly que tem a fazer referência a implementação do .NET Framework e o .NET Framework para Silverlight implementação de um assembly de referência específica. Por exemplo, um designer XAML gravado no Windows Presentation Foundation (WPF) talvez seja necessário fazer referência a área de trabalho do WPF implementação, para interface do usuário do designer e o subconjunto de WPF que está incluído na implementação do Silverlight. Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes. Este elemento desativa o comportamento padrão e permite que a compilação seja bem-sucedida.  
  
> [!IMPORTANT]
>  Para o compilador passar as informações a lógica de associação de assembly do common language runtime, você deve usar o `/appconfig` opção de compilador para especificar o local do arquivo App. config que contém este elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir permite que um aplicativo têm referências a implementação do .NET Framework e o .NET Framework para Silverlight implementação de qualquer assembly do .NET Framework que existe em ambas as implementações. O `/appconfig` opção de compilador deve ser usada para especificar o local do arquivo App. config.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [/AppConfig (opções do compilador c#)](http://msdn.microsoft.com/library/ee523958.aspx)  
 [Visão geral do .NET framework Assembly Unificação](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
