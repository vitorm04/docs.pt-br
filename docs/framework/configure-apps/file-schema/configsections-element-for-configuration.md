---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6024144b6f12df22369366f04c3cbad02c5011d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119014"
---
# <a name="configsections-element-for-configuration"></a>\<configSections > elemento para \<configuração >

Contém as declarações de namespace e seção de configuração.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<configsections >**

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [ **\<seção >** ](section-element.md) | Contém uma declaração de seção de configuração. |
| [ **\<> de seção**](sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |
| [ **\<remove>** ](remove-element-for-configsections.md) | Remove uma seção ou um grupo de seções predefinido. |
| [ **\<clear>** ](clear-element-for-configsections.md) | Limpa todas as seções e grupos de seções definidos anteriormente. |

## <a name="remarks"></a>Comentários

Se esse elemento estiver em um arquivo de configuração, ele deverá ser o primeiro elemento filho do elemento **\<configuration >** .

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
