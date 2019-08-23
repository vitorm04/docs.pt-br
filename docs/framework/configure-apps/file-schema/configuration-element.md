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
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921247"
---
# <a name="configuration-element"></a>\<elemento de > de configuração

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
| [ **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md) | Especifica a diretiva de ligação de assembly no nível de configuração.|
| [esquema de configurações de > de inicialização  **\<** ](./startup/index.md) | Todos os elementos no esquema de configurações de inicialização. |
| [esquema de configurações de > de tempo de execução  **\<** ](./runtime/index.md) | Todos os elementos no esquema de configurações de tempo de execução. |
| [ **\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Todos os elementos no esquema de configurações de comunicação remota. |
| [esquema de configurações do **System .net > \<** ](./network/index.md) | Todos os elementos no esquema de configurações de rede. |
| [esquema de configurações de > de cryptographySettings  **\<** ](./cryptography/index.md) | Todos os elementos no esquema de configurações de criptografia. |
| [esquema de seções de > de configuração  **\<** ](configuration-sections-schema.md) | Todos os elementos na seção de configuração esquema de configurações. |
| [Esquema de configurações de rastreamento e depuração](./trace-debug/index.md) | Todos os elementos no esquema de configurações de rastreamento e depuração. |
| [Esquema de definições de configuração do ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Todos os elementos no esquema de configuração do ASP.NET, que incluem elementos para configurar sites e aplicativos do ASP.NET. Usado em arquivos *Web. config* . |
| [esquema de configurações de > de WebServices  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Todos os elementos no esquema de configurações de serviços Web. |
| [Esquema de configurações Web](./web/index.md) | Todos os elementos do esquema de configurações da Web, que incluem elementos para configurar como o ASP.NET, funciona com um aplicativo host, como o IIS. Usado em arquivos *ASPNET. config* . |

## <a name="remarks"></a>Comentários

Cada arquivo de configuração deve conter exatamente  **\<** um elemento de > de configuração.

## <a name="see-also"></a>Consulte também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
