---
title: Elemento <linkedConfiguration>
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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921010"
---
# <a name="linkedconfiguration-element"></a>\<elemento de > linkedConfiguration

Especifica um arquivo de configuração a ser incluído.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**

## <a name="syntax"></a>Sintaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atributo

|           | Descrição |
| --------- | ----------- |
| **href**  | Atributo obrigatório.<br><br>A URL do arquivo de configuração a ser incluído. O único formato com suporte para o atributo href `file://`é. Há suporte para arquivos locais e arquivos UNC. |

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [elemento de > assemblyBinding  **\<** ](assemblybinding-element-for-configuration.md) | Especifica a diretiva de ligação de assembly no nível de configuração. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="remarks"></a>Comentários

O elemento  **\<> linkedConfiguration** simplifica a manutenção de assemblies de componente. Se um ou mais aplicativos usarem um assembly que tenha um arquivo de configuração que resida em um local bem conhecido, os arquivos de configuração dos aplicativos que usam o assembly poderão usar o  **\<elemento > linkedConfiguration** para incluir o arquivo de configuração do assembly, em vez de incluir informações de configuração diretamente. Quando o assembly de componente é atendido, a atualização do arquivo de configuração comum fornece informações de configuração atualizadas para todos os aplicativos que usam o assembly.

> [!NOTE]
> O elemento de  **\<> linkedConfiguration** não tem suporte para aplicativos com manifestos lado a lado do Windows.

As regras a seguir regem o uso de arquivos de configuração vinculados:

- As configurações nos arquivos de configuração incluídos afetam apenas a política de associação do carregador e são usadas somente pelo carregador. Os arquivos de configuração incluídos podem ter configurações diferentes de diretivas de associação, mas essas configurações não têm nenhum efeito.

- O único formato com suporte para `href` o atributo `file://`é. Há suporte para arquivos locais e arquivos UNC.

- Não há nenhuma restrição quanto ao número de configurações vinculadas por arquivo de configuração.

- Todos os arquivos de configuração vinculados são mesclados para formar um arquivo, semelhante ao comportamento `#include` da diretiva em CC++/.

- **O\<elemento > linkedConfiguration** é permitido somente em arquivos de configuração de aplicativo; ele é ignorado em *Machine. config*.

- Referências circulares são detectadas e terminadas. Ou seja, se o  **\<linkedConfiguration >** elementos de uma série de arquivos de configuração formam um loop, o loop será detectado e interrompido.

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

- [elemento de > assemblyBinding  **\<** ](assemblybinding-element-for-configuration.md)
- [Esquema do arquivo de configuração para o .NET Framework](index.md)
