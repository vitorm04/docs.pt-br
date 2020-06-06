---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155343"
---
# <a name="configsections-element-for-configuration"></a>Elemento \<configSections> para \<configuration>

Contém as declarações de namespace e seção de configuração.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<section>**](section-element.md) | Contém uma declaração de seção de configuração. |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |
| [**\<remove>**](remove-element-for-configsections.md) | Remove uma seção ou um grupo de seções predefinido. |
| [**\<clear>**](clear-element-for-configsections.md) | Limpa todas as seções e grupos de seções definidos anteriormente. |

## <a name="remarks"></a>Comentários

Se esse elemento estiver em um arquivo de configuração, ele deverá ser o primeiro elemento filho do **\<configuration>** elemento.

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

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
