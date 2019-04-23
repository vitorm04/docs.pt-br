---
title: Elemento <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc26f9721e911e05c5b5d4092be21a4e1191c84
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183932"
---
# <a name="supportportability-element"></a>\<supportPortability > elemento
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
|PKT|Atributo obrigatório.<br /><br /> Especifica o token de chave pública do assembly afetado, como uma cadeia de caracteres.|  
|habilitado|Atributo opcional.<br /><br /> Especifica se o suporte à portabilidade entre implementações do assembly do .NET Framework especificado deve ser habilitado.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Habilite o suporte para portabilidade entre implementações do assembly do .NET Framework especificado. Esse é o padrão.|  
|false|Desabilite o suporte para portabilidade entre implementações do assembly do .NET Framework especificado. Isso permite que o aplicativo tenha referências às várias implementações do assembly especificado.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], suporte é fornecido automaticamente para aplicativos que podem usar qualquer uma das duas implementações do .NET Framework, por exemplo uma implementação do .NET Framework ou .NET Framework para implementação do Silverlight. As duas implementações de um determinado assembly do .NET Framework são consideradas como equivalentes pelo associador do assembly. Em alguns cenários, esse recurso de portabilidade do aplicativo causa problemas. Nesses cenários, o `<supportPortability>` elemento pode ser usado para desabilitar o recurso.  
  
 Um cenário é um assembly que tem a fazer referência a implementação do .NET Framework e o .NET Framework para implementação do Silverlight de um assembly de referência específico. Por exemplo, um designer XAML escrito no Windows Presentation Foundation (WPF) talvez seja necessário fazer referência a ambos os a implementação de área de trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF que está incluído na implementação do Silverlight. Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes. Esse elemento desabilita o comportamento padrão e permite que a compilação seja bem-sucedida.  
  
> [!IMPORTANT]
>  Para que o compilador passar as informações à lógica de associação de assembly do common language runtime, você deve usar o `/appconfig` opção de compilador para especificar o local do arquivo App. config que contém esse elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir permite que um aplicativo tenha referências à implementação do .NET Framework e o .NET Framework para implementação do Silverlight de qualquer assembly do .NET Framework que exista em ambas as implementações. O `/appconfig` opção de compilador deve ser usada para especificar o local desse arquivo App. config.  
  
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

- [/AppConfig (opções do compilador c#)](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [Visão geral da Unificação de assemblies do framework .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
