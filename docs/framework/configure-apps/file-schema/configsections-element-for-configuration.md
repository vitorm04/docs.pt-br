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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155343"
---
# <a name="configsections-element-for-configuration"></a>\<configureSes> \<elemento para configuração>

Contém seção de configuração e declarações de namespace.

configuração &nbsp; &nbsp; [** \<>**](configuration-element.md) ** \<configuraçãoSeções>**

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [**\<>de configuração**](configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework. |

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<>de seção**](section-element.md) | Contém uma declaração de seção de configuração. |
| [**\<>de sectionGroup**](sectiongroup-element-for-configsections.md) | Define um namespace para seções de configuração. |
| [**\<remover>**](remove-element-for-configsections.md) | Remove uma seção ou grupo de seção predefinido. |
| [**\<claro>**](clear-element-for-configsections.md) | Limpa todas as seções e grupos de seção previamente definidos. |

## <a name="remarks"></a>Comentários

Se este elemento estiver em um arquivo de configuração, ele deve ser o primeiro elemento filho do ** \<elemento>configuração.**

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração e definir configurações para essa seção:

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

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema de arquivo de configuração para o Framework .NET](index.md)
