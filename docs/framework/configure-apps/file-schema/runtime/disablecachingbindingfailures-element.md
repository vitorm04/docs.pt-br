---
title: '&lt;disableCachingBindingFailures&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20cc7e37b2ea66cae9f28367f97b69ed43f1a13e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543861"
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disableCachingBindingFailures&gt; elemento
Especifica se é necessário desabilitar o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<disableCachingBindingFailures>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|habilitado|Atributo obrigatório.<br /><br /> Especifica se é necessário desabilitar o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Não desabilite o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação. Esse é o comportamento de associação padrão começando com o .NET Framework versão 2.0.|  
|1|Desabilite o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação. Essa configuração será revertido para o comportamento de associação do .NET Framework versão 1.1.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework versão 2.0, o comportamento padrão de carregamento de assemblies é armazenar em cache todos os associação e falhas de carregamento. Ou seja, se uma tentativa de carregar um assembly falhar, as solicitações subsequentes para carregar o mesmo assembly falham imediatamente, sem qualquer tentativa de localizar o assembly. Esse elemento desabilita o comportamento padrão para falhas que ocorrem porque o assembly não pôde ser encontrado no caminho de investigação de associação. Essas falhas lançar <xref:System.IO.FileNotFoundException>.  
  
 Alguns associação e falhas de carregamento não são afetados por este elemento e sempre são armazenados em cache. Essas falhas ocorrem porque o assembly foi encontrado, mas não pôde ser carregado. Elas geram <xref:System.BadImageFormatException> ou <xref:System.IO.FileLoadException>. A lista a seguir inclui alguns exemplos de tais falhas.  
  
-   Se você tentar carregar um arquivo não é um assembly válido, as tentativas subsequentes para carregar o assembly falhará mesmo se o arquivo inválido é substituído com o assembly correto.  
  
-   Se você tentar carregar um assembly que está bloqueado pelo sistema de arquivos, as tentativas subsequentes para carregar o assembly falhará mesmo depois que o assembly é liberado pelo sistema de arquivos.  
  
-   Se uma ou mais versões do assembly que você está tentando carregar está no caminho de investigação, mas a versão específica que você está solicitando não está entre eles, tentativas subsequentes para carregar dessa versão falhará, mesmo se a versão correta é movida para o caminho de investigação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar o cache de falhas de associação de assembly que ocorrem porque o assembly não foi encontrado por sondagem.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
