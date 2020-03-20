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
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154303"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<montagemElemento> \<de identidade para> de tempo de execução
Contém informações de identificação sobre a montagem.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<montagem>vinculante**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependente>de montagem**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<montagemIdentidade>**  
  
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
|`name`|Atributo obrigatório.<br /><br /> O nome da assembléia|  
|`culture`|Atributo opcional.<br /><br /> Uma seqüência que especifica o idioma e o país/região da montagem.|  
|`publicKeyToken`|Atributo opcional.<br /><br /> Um valor hexadecimal que especifica o nome forte da montagem.|  
|`processorArchitecture`|Atributo opcional.<br /><br /> Um dos valores "x86", "amd64", "msil" ou "ia64", especificando a arquitetura do processador para um conjunto que contém código específico do processador. Os valores não são sensíveis a maiúsculas e minúsculas. Se o atributo for atribuído a `<assemblyIdentity>` qualquer outro valor, todo o elemento será ignorado. Consulte <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>atributo de arquitetura do processador  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`amd64`|Somente arquitetura AMD x86-64.|  
|`ia64`|Somente arquitetura Intel Itanium.|  
|`msil`|Neutro em relação ao processador e bits por palavra.|  
|`x86`|Um processador x86 de 32 bits, nativo ou no ambiente Windows on Windows (WOW) em uma plataforma de 64 bits.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`dependentAssembly`|Encapsula local do assembly e política de associação para cada assembly. Use `<dependentAssembly>` um elemento para cada montagem.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Cada ** \<** elemento de>de montagem dependente deve ter um ** \<elemento de>** filho de uma montagem.  
  
 Se `processorArchitecture` o atributo `<assemblyIdentity>` estiver presente, o elemento se aplica apenas ao conjunto com a arquitetura correspondente do processador. Se `processorArchitecture` o atributo não `<assemblyIdentity>` estiver presente, o elemento pode ser aplicado a um conjunto com qualquer arquitetura do processador.  
  
 O exemplo a seguir mostra um arquivo de configuração para dois conjuntos com o mesmo nome que visam duas arquiteturas diferentes de dois processadores, e cujas versões não foram mantidas em sincronia. Quando o aplicativo é executado na plataforma `<assemblyIdentity>` x86, o primeiro elemento se aplica e o outro é ignorado. Se o aplicativo for executado em uma plataforma diferente de x86 ou ia64, ambos serão ignorados.  
  
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
  
 Se um arquivo `<assemblyIdentity>` de configuração contiver um elemento sem `processorArchitecture` atributo e `processorArchitecture` não contiver um elemento que corresponda à plataforma, o elemento sem o atributo será usado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como fornecer informações sobre uma montagem.  
  
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
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Redirecionando versões de assembly](../../redirect-assembly-versions.md)
