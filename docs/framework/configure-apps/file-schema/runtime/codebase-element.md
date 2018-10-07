---
title: '&lt;Base de código&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d7563d3a0ba545bfd8d1b80981fcce607d230873
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847276"
---
# <a name="ltcodebasegt-element"></a>&lt;Base de código&gt; elemento
Especifica onde o common language runtime pode encontrar um assembly.  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<dependentAssembly >  
\<Base de código >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`href`|Atributo obrigatório.<br /><br /> Especifica a URL onde o tempo de execução pode encontrar a versão especificada do assembly.|  
|`version`|Atributo obrigatório.<br /><br /> Especifica a versão do assembly a que a base de código aplica-se. O formato de um número de versão do assembly é *Major*.|  
  
## <a name="version-attribute"></a>Atributo de versão  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Para cada parte do número de versão, os valores válidos são 0 a 65535.|Não aplicável.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`buildproviders`|Define uma coleção de provedores de compilação usado para compilar os arquivos de recurso personalizado. Você pode ter qualquer número de provedores de compilação.|  
|`compilation`|Configura todas as configurações de compilação que o ASP.NET usa.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`System.web`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
 Para o tempo de execução usar o  **\<codeBase >** configuração em um arquivo de configuração do computador ou arquivo de política de editor, o arquivo também deve redirecionar a versão do assembly. Arquivos de configuração de aplicativo podem ter uma configuração de base de código sem redirecionar a versão do assembly. Depois de determinar qual versão de assembly a ser usada, o tempo de execução se aplica a configuração de base de código do arquivo que determina a versão. Se nenhuma base de código estiver indicado, o tempo de execução investiga o assembly como de costume.  
  
 Se o assembly tiver um nome forte, a configuração de base de código pode estar em qualquer lugar na intranet local ou na Internet. Se o assembly é um assembly particular, a configuração de base de código deve ser um caminho relativo ao diretório do aplicativo.  
  
 Para assemblies sem um nome forte, a versão é ignorado e o carregador usará a primeira ocorrência desse \<codebase > dentro de \<dependentAssembly >. Se houver uma entrada no arquivo de configuração do aplicativo que redireciona associação a outro assembly, o redirecionamento terá precedência mesmo se a versão do assembly não corresponde a solicitação de associação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar onde o tempo de execução pode encontrar um assembly.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Especificando o local de um assembly](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
