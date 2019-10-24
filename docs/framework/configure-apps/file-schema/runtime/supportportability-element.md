---
title: Elemento <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a76c378038a19d3edb9fe0c5e61012cc854c1b7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773926"
---
# <a name="supportportability-element"></a>\<supportPortability elemento >
Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) > \
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \<supportPortability **>**  
  
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
|habilitado|Atributo opcional.<br /><br /> Especifica se o suporte para portabilidade entre as implementações do assembly de .NET Framework especificado deve ser habilitado.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Habilite o suporte para portabilidade entre implementações do assembly de .NET Framework especificado. Esse é o padrão.|  
|false|Desabilite o suporte para portabilidade entre implementações do assembly de .NET Framework especificado. Isso permite que o aplicativo tenha referências a várias implementações do assembly especificado.|  
  
### <a name="child-elements"></a>Elementos filho  

nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
  
## <a name="remarks"></a>Comentários  

A partir do .NET Framework 4, o suporte é fornecido automaticamente para aplicativos que podem usar uma das duas implementações do .NET Framework, por exemplo, a implementação do .NET Framework ou o .NET Framework para a implementação do Silverlight. As duas implementações de um determinado assembly de .NET Framework são vistas como equivalentes pelo associador de assembly. Em alguns cenários, esse recurso de portabilidade de aplicativo causa problemas. Nesses cenários, o elemento `<supportPortability>` pode ser usado para desabilitar o recurso.  
  
Um cenário desse tipo é um assembly que tem que referenciar a implementação de .NET Framework e o .NET Framework para a implementação do Silverlight de um determinado assembly de referência. Por exemplo, um designer XAML escrito em Windows Presentation Foundation (WPF) pode precisar referenciar a implementação da área de trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF que está incluído na implementação do Silverlight. Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes. Esse elemento desabilita o comportamento padrão e permite que a compilação tenha sucesso.  
  
> [!IMPORTANT]
> Para que o compilador passe as informações para a lógica de associação de assembly do Common Language Runtime, você deve usar a opção de compilador `/appconfig` para especificar o local do arquivo app. config que contém esse elemento.  
  
## <a name="example"></a>Exemplo  

O exemplo a seguir permite que um aplicativo tenha referências para a implementação de .NET Framework e o .NET Framework para a implementação do Silverlight de qualquer assembly .NET Framework que exista em ambas as implementações. A opção de compilador `/appconfig` deve ser usada para especificar o local deste arquivo app. config.  
  
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

- [-appconfig (opções do compilador do C#)](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [Visão geral da unificação do assembly .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
