---
title: Elemento <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 9a7b25c74763c020c0e19c3f6099db9001acf773
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705409"
---
# <a name="configuration-element"></a>\<Configuração > elemento

O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.

**\<configuration>**

## <a name="syntax"></a>Sintaxe

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Atributos

Nenhum

## <a name="parent-element"></a>Elemento pai

Nenhum

## <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Especifica a diretiva de ligação de assembly no nível de configuração.|
| [**\<inicialização >** esquema de configurações](~/docs/framework/configure-apps/file-schema/startup/index.md) | Todos os elementos no esquema de configurações de inicialização. |
| [**\<tempo de execução >** esquema de configurações](~/docs/framework/configure-apps/file-schema/runtime/index.md) | Todos os elementos no esquema de configurações de tempo de execução. |
| [**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Todos os elementos no esquema de configurações de comunicação remota. |
| [**\<system.Net>** Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) | Todos os elementos no esquema de configurações de rede. |
| [**\<cryptographySettings>** Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Todos os elementos no esquema de configurações de criptografia. |
| [**\<Configuração >** esquema de seções](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Todos os elementos no esquema de configurações da seção de configuração. |
| [Esquema de configurações de rastreamento e depuração](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | Todos os elementos no esquema de configurações de rastreamento e depuração. |
| [Esquema de configurações de configuração do ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Todos os elementos no esquema de configuração de ASP.NET, que inclui elementos para configurar sites e aplicativos Web do ASP.NET. Usado na *Web. config* arquivos. |
| [**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Todos os elementos no esquema de configurações de serviços da Web. |
| [Esquema de configurações Web](~/docs/framework/configure-apps/file-schema/web/index.md) | Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS. Usado na *ASPNET* arquivos. |

## <a name="remarks"></a>Comentários

Cada arquivo de configuração deve conter exatamente um  **\<configuration >** elemento.

## <a name="see-also"></a>Consulte também

- [Esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
