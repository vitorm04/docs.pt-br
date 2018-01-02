---
title: '&lt;enforceFIPSPolicy&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb8cb1ea4d011eb25aee14ddd53d3dc882f75d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforceFIPSPolicy&gt; elemento
Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<enforceFIPSPolicy > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Habilitado|Atributo obrigatório.<br /><br /> Especifica se deseja habilitar a aplicação de um requisito de configuração do computador que os algoritmos de criptografia devem ser compatíveis com FIPS.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`true`|Se o computador está configurado para exigir que os algoritmos de criptografia para ser compatível com FIPS, esse requisito é imposto. Se uma classe implementa um algoritmo que não é compatível com FIPS, construtores ou `Create` métodos para essa classe lançam exceções quando eles são executados no computador. Esse é o padrão.|  
|`false`|Algoritmos de criptografia que são usados pelo aplicativo não são necessários para serem compatíveis com FIPS, independentemente da configuração do computador.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 2.0, a criação de classes que implementam algoritmos de criptografia é controlada pela configuração do computador. Se o computador está configurado para exigir algoritmos compatíveis com FIPS, e uma classe implementa um algoritmo que não é compatível com FIPS, qualquer tentativa de criar uma instância dessa classe gera uma exceção. Construtores lançar um <xref:System.InvalidOperationException> exceção, e `Create` métodos lançam uma <xref:System.Reflection.TargetInvocationException> exceção com uma interna <xref:System.InvalidOperationException> exceção.  
  
 Se seu aplicativo é executado nos computadores cujas configurações requerem a conformidade com FIPS, e seu aplicativo usa um algoritmo que não é compatível com FIPS, você pode usar esse elemento no arquivo de configuração para impedir que o common language runtime (CLR) do imposição de conformidade FIPS. Esse elemento foi introduzido no [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como impedir que o CLR imposição de conformidade FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Modelo de criptografia](../../../../../docs/standard/security/cryptography-model.md)
