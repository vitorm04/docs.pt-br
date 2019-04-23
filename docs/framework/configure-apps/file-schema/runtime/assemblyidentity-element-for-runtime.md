---
title: Elemento <assemblyIdentity> para <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: d5766b76f18dce441cb260887a753dcf64642a6f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098689"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblyIdentity > elemento para \<tempo de execução >
Contém informações de identificação sobre o assembly.  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<dependentAssembly>  
\<assemblyIdentity>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Atributo obrigatório.<br /><br /> O nome do assembly|  
|`culture`|Atributo opcional.<br /><br /> Uma cadeia de caracteres que especifica o idioma e país/região do assembly.|  
|`publicKeyToken`|Atributo opcional.<br /><br /> Um valor hexadecimal que especifica o nome forte do assembly.|  
|`processorArchitecture`|Atributo opcional.<br /><br /> Um dos valores "x86", "amd64", "msil" ou "ia64", especificando a arquitetura do processador para um assembly que contém o código específico do processador. Os valores não diferenciam maiusculas de minúsculas. Se o atributo é atribuído a qualquer outro valor, toda a `<assemblyIdentity>` elemento será ignorado. Consulte <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`amd64`|AMD 64 x86 somente a arquitetura.|  
|`ia64`|Somente arquitetura Intel Itanium.|  
|`msil`|Neutro em relação ao processador e bits por palavra.|  
|`x86`|Um x86 de 32 bits processador, nativo ou no Windows no ambiente do Windows (WOW) em uma plataforma de 64 bits.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`dependentAssembly`|Encapsula local do assembly e política de associação para cada assembly. Use um `<dependentAssembly>` elemento para cada assembly.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Cada  **\<dependentAssembly >** elemento deve ter uma  **\<assemblyIdentity >** elemento filho.  
  
 Se o `processorArchitecture` atributo estiver presente, o `<assemblyIdentity>` elemento se aplica apenas ao assembly com a arquitetura do processador correspondente. Se o `processorArchitecture` atributo não estiver presente, o `<assemblyIdentity>` elemento pode ser aplicado a um assembly com qualquer arquitetura de processador.  
  
 O exemplo a seguir mostra um arquivo de configuração para dois assemblies com o mesmo nome que tenham como alvo duas diferentes arquiteturas de processador dois e cujas versões não tem sido mantidas em sincronia. Quando o aplicativo é executado em x86 plataforma primeiro `<assemblyIdentity>` elemento se aplica e o outro é ignorado. Se o aplicativo é executado em uma plataforma diferente x86 ou ia64, ambos serão ignoradas.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Se um arquivo de configuração contém um `<assemblyIdentity>` elemento sem nenhuma `processorArchitecture` de atributos e não contém um elemento que corresponda à plataforma, o elemento sem o `processorArchitecture` atributo é usado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como fornecer informações sobre um assembly.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Redirecionando versões de assembly](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
