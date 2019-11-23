---
title: Elemento <requiredRuntime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697494"
---
# <a name="requiredruntime-element"></a>\<elemento de > requiredRuntime

Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Este elemento foi preterido e não deve mais ser usado. O elemento [`supportedRuntime`](supportedruntime-element.md) deve ser usado em seu lugar.

[ **\<configuration>** ](../configuration-element.md)  
&nbsp;de inicialização do &nbsp;[ **\<>** ](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<requiredRuntime >**  

## <a name="syntax"></a>Sintaxe

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`version`|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a versão do .NET Framework ao qual esse aplicativo dá suporte. O valor da cadeia de caracteres deve corresponder ao nome do diretório encontrado na raiz de instalação do .NET Framework. O conteúdo do valor da cadeia de caracteres não é analisado.|
|`safemode`|Atributo opcional.<br /><br /> Especifica se o código de inicialização do tempo de execução pesquisa o registro para determinar a versão de tempo de execução.|

## <a name="safemode-attribute"></a>atributo de modo de adficar

|Valor|Descrição|
|-----------|-----------------|
|`false`|O código de inicialização do tempo de execução procura no registro. Este é o valor padrão.|
|`true`|O código de inicialização do tempo de execução não procura no registro.|

### <a name="child-elements"></a>Child elements

None.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`startup`|Contém o elemento `<requiredRuntime>`.|

## <a name="remarks"></a>Comentários
 Os aplicativos criados para dar suporte apenas à versão 1,0 do tempo de execução devem usar o elemento `<requiredRuntime>`. Os aplicativos criados usando a versão 1,1 ou posterior do tempo de execução devem usar o elemento `<supportedRuntime>`.

> [!NOTE]
> Se você usar a função [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração, deverá usar o elemento `<requiredRuntime>` para todas as versões do tempo de execução. O elemento `<supportedRuntime>` é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 A cadeia de caracteres do atributo `version` deve corresponder ao nome da pasta de instalação para a versão especificada do .NET Framework. Essa cadeia de caracteres não é interpretada. Se o código de inicialização do tempo de execução não encontrar uma pasta correspondente, o tempo de execução não será carregado; o código de inicialização mostra uma mensagem de erro e é encerrado.

> [!NOTE]
> O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignora o elemento `<requiredRuntime>`.

## <a name="example"></a>{1&gt;Exemplo&lt;1}

O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Esquema de configurações de inicialização](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Como configurar um aplicativo para dar suporte a .NET Framework 4 ou versões posteriores](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
