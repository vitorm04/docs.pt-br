---
title: Elemento <clear> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d321f3169344e9aa40d65b1722a533549de5315a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088730"
---
# <a name="clear-element-for-appsettings"></a>\<limpar > elemento para \<appSettings >

Limpa as configurações de aplicativo personalizadas.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<desmarque >**

## <a name="syntax"></a>Sintaxe

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

|     | Descrição |
| --- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço Web XML ou qualquer outra informação de configuração de aplicativo personalizada. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como limpar as definições de configuração personalizadas:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](../index.md)
