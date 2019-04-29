---
title: Elemento <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aa958e15449949a1b7ca740198fff71295b2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704954"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy > elemento
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
|habilitado|Atributo obrigatório.<br /><br /> Especifica se deseja habilitar a imposição de um requisito de configuração do computador que os algoritmos de criptografia devem ser compatíveis com FIPS.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`true`|Se o computador está configurado para exigir que os algoritmos de criptografia seja compatível com FIPS, esse requisito é imposto. Se uma classe implementa um algoritmo que não está em conformidade com FIPS, os construtores ou `Create` métodos dessa classe lançam exceções quando eles são executados no computador em questão. Esse é o padrão.|  
|`false`|Algoritmos de criptografia que são usados pelo aplicativo não são necessários para estar em conformidade com FIPS, independentemente da configuração do computador.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 2.0, a criação de classes que implementam algoritmos de criptografia é controlada pela configuração do computador. Se o computador está configurado para exigir que os algoritmos em conformidade com FIPS, e uma classe implementa um algoritmo que não está em conformidade com FIPS, qualquer tentativa de criar uma instância dessa classe gera uma exceção. Construtores lançar uma <xref:System.InvalidOperationException> exceção, e `Create` métodos geram uma <xref:System.Reflection.TargetInvocationException> exceção com uma interna <xref:System.InvalidOperationException> exceção.  
  
 Se seu aplicativo é executado em computadores cujas configurações exigem a conformidade com FIPS, e seu aplicativo usa um algoritmo que não está em conformidade com FIPS, você pode usar esse elemento no arquivo de configuração para impedir que o common language runtime (CLR) do impor a conformidade com FIPS. Esse elemento foi introduzido no [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como evitar que o CLR de impor a conformidade FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Modelo de criptografia](../../../../../docs/standard/security/cryptography-model.md)
