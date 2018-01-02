---
title: "&lt;assemblyIdentity&gt; elemento para &lt;tempo de execução&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0dadf0e07f5e3a9f9152ae7cd57c62721402bff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;assemblyIdentity&gt; elemento para &lt;tempo de execução&gt;
Contém informações de identificação sobre o assembly.  
  
 \<configuration>  
\<tempo de execução >  
\<assemblyBinding >  
\<dependentAssembly >  
\<assemblyIdentity >  
  
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
|`processorArchitecture`|Atributo opcional.<br /><br /> Um dos valores de "x86", "amd64", "msil" ou "ia64", especificando a arquitetura do processador para um assembly que contém o código específico do processador. Os valores não diferenciam maiusculas de minúsculas. Se o atributo é atribuído a qualquer outro valor, todo o `<assemblyIdentity>` elemento será ignorado. Consulte <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`amd64`|Apenas um processador AMD da 64 bits.|  
|`ia64`|Apenas um processador da 64 bits.|  
|`msil`|Neutro em relação ao processador e bits por palavra|  
|`x86`|Um processador de 32 bits, ou nativo ou no Windows no ambiente do Windows (WOW) em uma plataforma de 64 bits.|  
  
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
 Cada  **\<dependentAssembly >** elemento deve ter um  **\<assemblyIdentity >** elemento filho.  
  
 Se o `processorArchitecture` atributo estiver presente, o `<assemblyIdentity>` elemento se aplica somente ao assembly com a arquitetura de processador correspondente. Se o `processorArchitecture` atributo não estiver presente, o `<assemblyIdentity>` elemento pode ser aplicado a um assembly com qualquer arquitetura de processador.  
  
 O exemplo a seguir mostra um arquivo de configuração para dois assemblies com o mesmo nome de destino diferentes duas duas arquiteturas de processador e cujas versões não tem sido mantidas em sincronia. Quando o aplicativo executa em x86 plataforma primeiro `<assemblyIdentity>` elemento se aplica e a outra é ignorada. Se o aplicativo é executado em uma plataforma que não seja x86 ou ia64, ambos serão ignoradas.  
  
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
  
 Se um arquivo de configuração contém uma `<assemblyIdentity>` elemento sem nenhum `processorArchitecture` de atributos e não contém um elemento que corresponda à plataforma, o elemento sem o `processorArchitecture` atributo será usado.  
  
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
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Redirecionando versões de assembly](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
