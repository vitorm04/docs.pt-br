---
title: '&lt;useLegacyJit&gt; elemento'
ms.custom: 
ms.date: 04/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 735733fc33a21c2f275c1ea9894c43558f01626e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltuselegacyjitgt-element"></a>&lt;useLegacyJit&gt; elemento

Determina se o Common Language Runtime usa o compilador JIT de 64 bits herdado para uma compilação just-in-time.  
  
\<configuration>  
\<tempo de execução >  
\<useLegacyJit >
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<useLegacyJit enabled=0|1 />
```

O nome do elemento `useLegacyJit` diferencia maiusculas de minúsculas.
  
## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
| Atributo | Descrição                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Atributo obrigatório.<br><br>Especifica se o tempo de execução usa o compilador JIT 64-bit herdado. |  
  
### <a name="enabled-attribute"></a>atributo habilitado  
  
| Valor | Descrição                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | O common language runtime usa o novo compilador JIT de 64 bits incluído no .NET Framework 4.6 e versões posteriores. |  
| 1     | O common language runtime usa o compilador JIT de 64 bits mais antigo.                                                     |  
  
### <a name="child-elements"></a>Elementos filho

Nenhum
  
### <a name="parent-elements"></a>Elementos pai  
  
| Elemento         | Descrição                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |  
| `runtime`       | Contém informações sobre opções de inicialização do tempo de execução.                                                        |  
  
## <a name="remarks"></a>Comentários  

Começando com o .NET Framework 4.6, o common language runtime usa um novo compilador de 64 bits para compilação Just-in-(JIT) por padrão. Em alguns casos, isso pode resultar em uma diferença no comportamento do código do aplicativo que foi compilado por JIT por versões anteriores do compilador JIT 64 bits. Definindo o `enabled` atributo do `<useLegacyJit>` elemento `1`, você pode desabilitar o novo compilador JIT 64-bit e em vez disso, compile seu aplicativo usando o compilador JIT 64-bit herdado.  
  
> [!NOTE]
> O `<useLegacyJit>` elemento afeta apenas a compilação JIT em 64 bits. Compilação com o compilador JIT de 32 bits não é afetada.  
  
Em vez de usar uma configuração de arquivo de configuração, você pode habilitar o compilador JIT herdado 64-bit em duas outras maneiras:  
  
- Definindo uma variável de ambiente

  Definir o `COMPLUS_useLegacyJit` variável de ambiente para o `0` (use o novo compilador JIT 64 bits) ou `1` (use o compilador JIT 64 bits mais antigo):
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  A variável de ambiente tem *escopo global*, que significa que ele afeta todos os aplicativos executados no computador. Se definido, ele pode ser substituído pelo parâmetro de arquivo de configuração do aplicativo. O nome da variável de ambiente não diferencia maiusculas de minúsculas.
  
- Adicionar uma chave do registro

  Você pode habilitar o compilador JIT 64-bit herdado adicionando um `REG_DWORD` valor como o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` ou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chave no registro. O valor é denominado `useLegacyJit`. Se o valor for 0, o compilador novo será usado. Se o valor for 1, o compilador JIT 64-bit herdado está habilitado. O nome do valor do registro não diferencia maiusculas de minúsculas.
  
  Adicionando o valor para o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` chave afeta todos os aplicativos em execução no computador. Adicionando o valor para o `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chave afeta todos os aplicativos executados pelo usuário atual. Se um computador é configurado com várias contas de usuário, somente os aplicativos executados pelo usuário atual são afetados, a menos que o valor é adicionado para as chaves do registro para outros usuários. Adicionando o `<useLegacyJit>` elemento para um arquivo de configuração substitui as configurações do registro, se elas estiverem presentes.  
  
## <a name="example"></a>Exemplo  

O arquivo de configuração a seguir desabilita a compilação com o novo compilador JIT 64-bit e em vez disso, usa o compilador JIT 64-bit herdado.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

[\<tempo de execução > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
[\<Configuração > elemento](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
[Mitigação: novo compilador JIT de 64 bits](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
