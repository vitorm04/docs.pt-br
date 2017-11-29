---
title: '&lt;codeBase&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b30f1dc3ccade3028c31c57ffdab521802f086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcodebasegt-element"></a>&lt;codeBase&gt; elemento
Especifica onde o common language runtime pode encontrar um assembly.  
  
 \<configuration>  
\<tempo de execução >  
\<assemblyBinding >  
\<dependentAssembly >  
\<codeBase >  
  
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
|`version`|Atributo obrigatório.<br /><br /> Especifica a versão do assembly a que a base de código aplica-se. O formato de um número de versão do assembly é *Revision*.|  
  
## <a name="version-attribute"></a>versão de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Para cada parte do número de versão, os valores válidos são 0 a 65535.|Não aplicável.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`buildproviders`|Define uma coleção de provedores de compilação usada para compilar arquivos de recursos personalizados. Você pode ter qualquer número de provedores de compilação.|  
|`compilation`|Configura todas as configurações de compilação que o ASP.NET usa.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`System.web`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
 Para o tempo de execução usar o  **\<codeBase >** configuração em um arquivo de configuração de máquina ou arquivo de política de editor, o arquivo deve também redirecionar a versão do assembly. Arquivos de configuração do aplicativo podem ter uma configuração de base de código sem redirecionando a versão do assembly. Depois de determinar qual versão do assembly a ser usado, o tempo de execução se aplica a configuração de base de código do arquivo que determina a versão. Se nenhuma codebase é indicado, o tempo de execução de testes para o assembly como de costume.  
  
 Se o assembly tiver um nome forte, a configuração de base de código pode estar em qualquer lugar na intranet local ou na Internet. Se o assembly é um assembly privado, a configuração de base de código deve ser um caminho relativo ao diretório do aplicativo.  
  
 Para assemblies sem um nome forte, a versão é ignorada e o carregador usa a primeira ocorrência de \<codebase > dentro de \<dependentAssembly >. Se houver uma entrada no arquivo de configuração do aplicativo que redireciona a associação a outro assembly, o redirecionamento terá precedência, mesmo se a versão do assembly não corresponde a solicitação de associação.  
  
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
