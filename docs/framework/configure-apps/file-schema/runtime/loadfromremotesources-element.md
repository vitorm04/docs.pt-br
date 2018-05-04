---
title: '&lt;loadFromRemoteSources&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d442f71a0e2fc7deacd9aaa02cfba7b66f2349
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt; elemento
Especifica se assemblies de fontes remotas devem receber confiança total.  
  
> [!NOTE]
>  Se tiver sido direcionado a este tópico devido a uma mensagem de erro na lista de erros do projeto do Visual Studio ou um erro de compilação, consulte [como: usar um Assembly da Web no Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<configuration>  
\<runtime>  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se um assembly carregado a partir de fontes remotas deve receber confiança total.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não conceda confiança total para aplicativos de fontes remotas. Esse é o padrão.|  
|`true`|Conceder confiança total para aplicativos de fontes remotas.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 3.5 e versões anteriores, se você carregar um assembly de um local remoto, o assembly será executado parcialmente confiável com um conjunto de concessão que depende da zona em que ele foi carregado. Por exemplo, se você tiver carregado um assembly de um site, ele foi carregado na zona da Internet e concedido o conjunto de permissões de Internet. Em outras palavras, executado em uma área restrita de Internet. Se você tentar executar o assembly [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] e versões posteriores, uma exceção é lançada; você deve criar explicitamente uma área restrita para o assembly (consulte [como: executar código parcialmente confiável em uma área restrita](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), ou executá-lo em confiança total.  
  
 O `<loadFromRemoteSources>` permite que o elemento você especificar que os assemblies que executaria parcialmente confiável em versões anteriores do .NET Framework a ser executado totalmente confiáveis no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e versões posteriores. Por padrão, os assemblies remotos não são executados no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e posterior. Para executar um assembly remoto, você deve executá-lo como totalmente confiável ou criar uma área restrita <xref:System.AppDomain> na qual para executá-lo.  
  
> [!NOTE]
>  No [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies em compartilhamentos de rede local são executados em confiança total por padrão; você não precisa habilitar o `<loadFromRemoteSources>` elemento.  
  
> [!NOTE]
>  Se um aplicativo foi copiado da web, ele é marcado pelo Windows como sendo um aplicativo web, mesmo que ela reside no computador local. Você pode alterar essa designação alterando as propriedades de arquivo, ou você pode usar o `<loadFromRemoteSources>` elemento conceder o conjunto completo de confiança. Como alternativa, você pode usar o <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> método para carregar um assembly local que o sistema operacional foi sinalizada como tendo sido carregado da web.  
  
 O `enabled` atributo para este elemento é eficaz apenas quando a segurança de acesso ao código (CAS) está desabilitada. Por padrão, a política de CAS está desabilitada no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e versões posteriores. Se você definir `enabled` para `true`, aplicativos remotos recebem confiança total.  
  
 Se `<loadFromRemoteSources>``enabled` não está definido como `true`, uma exceção é lançada sob as seguintes condições:  
  
-   O comportamento de modo seguro do domínio atual é diferente de seu comportamento no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]. Isso requer a política de CAS será desabilitada e o domínio atual não deve ser em modo seguro.  
  
-   O assembly que está sendo carregado não é do `MyComputer` zona.  
  
> [!NOTE]
>  Você pode obter um <xref:System.IO.FileLoadException> em um aplicativo do Windows Virtual PC ao tentar carregar um arquivo de pastas vinculadas no computador host. Esse erro também pode ocorrer ao tentar carregar um arquivo de uma pasta vinculada por [dos serviços de área de trabalho remota](http://go.microsoft.com/fwlink/?LinkId=182775) (serviços de Terminal). Para evitar a exceção, defina `enabled` para `true`.  
  
 Definindo o `<loadFromRemoteSources>` elemento `true` impede esta exceção de que está sendo gerada. Ele permite que você especifique que você não depender de common language runtime para a área restrita de assemblies carregados para a segurança e que eles possam ter permissão para executar como total confiança.  
  
> [!IMPORTANT]
>  Se o assembly não deve ser executado em confiança total, não defina este elemento de configuração. Em vez disso, crie uma área restrita <xref:System.AppDomain> no qual carregar o assembly.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto. Para obter mais informações, consulte o artigo [mais implícita usa da política de CAS: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) no blog de segurança do .NET.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como conceder confiança total para aplicativos de fontes remotas.  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usa mais implícita da política de CAS: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [Como executar código parcialmente confiável em uma área restrita](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
