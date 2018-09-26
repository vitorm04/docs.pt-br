---
title: '&lt;linkedConfiguration&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c5186aa94993ba551252db6fef55853b5b554789
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200952"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > elemento

Especifica um arquivo de configuração a ser incluído.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**

## <a name="syntax"></a>Sintaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **href**  | Atributo obrigatório.<br><br>A URL do arquivo de configuração para incluir. O único formato com suporte para o **href** atributo é `file://`. Há suporte para arquivos locais e arquivos UNC. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<assemblyBinding >** elemento](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Especifica a diretiva de ligação de assembly no nível de configuração. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

O  **\<linkedConfiguration >** elemento simplifica a manutenção do assemblies do componente. Se um ou mais aplicativos usam um assembly que tem um arquivo de configuração que residem em um local conhecido, os arquivos de configuração dos aplicativos que usam o assembly podem usar o  **\<linkedConfiguration >** elemento para incluir o arquivo de configuração do assembly, em vez de incluindo informações de configuração diretamente. Quando o assembly do componente é atendido, atualizando o arquivo de configuração comum fornece informações de configuração atualizada para todos os aplicativos que usam o assembly.

> [!NOTE]
> O  **\<linkedConfiguration >** elemento não tem suporte para aplicativos com manifestos do Windows lado a lado.

As seguintes regras regem o uso de arquivos de configuração vinculados:

- As configurações em arquivos de configuração incluído só afetam a política de associação do carregador e são usadas somente pelo carregador de. Os arquivos de configuração incluído podem ter configurações diferentes políticas de associação, mas essas configurações não têm qualquer efeito.

- O único formato com suporte para o `href` atributo é `file://`. Há suporte para arquivos locais e arquivos UNC.

- Não há nenhuma restrição no número de configurações vinculadas por arquivo de configuração.

- Todos os arquivos de configuração vinculados são mesclados para formar um arquivo, semelhante ao comportamento da `#include` diretiva em C/C++.

- O  **\<linkedConfiguration >** elemento é permitido somente em arquivos de configuração do aplicativo; ele será ignorado na *Machine. config*.

- Referências circulares são detectadas e encerradas. Ou seja, se o  **\<linkedConfiguration >** elementos de uma série de arquivos de configuração formam um loop, o loop é detectado e interrompido.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como incluir o arquivo de configuração do disco rígido local:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Consulte também

[**\<assemblyBinding >** elemento](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
