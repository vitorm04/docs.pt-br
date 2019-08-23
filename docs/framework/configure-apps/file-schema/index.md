---
title: Esquema de arquivos de configuração para o .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921037"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Esquema de arquivos de configuração para o .NET Framework

Arquivos de configuração são arquivos XML padrão que você pode usar para alterar as configurações e definir diretivas para seus aplicativos. O esquema de configuração do .NET Framework consiste em elementos que você pode usar em arquivos de configuração para controlar o comportamento de seus aplicativos. O sumário desta seção reflete a hierarquia de esquema para inicialização, tempo de execução, rede e outros tipos de configuração.

Para obter informações sobre os tipos, o formato e o local dos arquivos de configuração, consulte o artigo [Configuring Apps](../index.md) (Configurando aplicativos). Familiarize-se com XML para editar os arquivos de configuração diretamente.

> [!IMPORTANT]
> Os atributos e as marcas XML em arquivos de configuração diferenciam maiúsculas de minúsculas.

## <a name="in-this-section"></a>Nesta seção

[Elemento **\<configuration>** ](configuration-element.md) Descreve o elemento `<configuration>`, que é o elemento de nível superior de todos os arquivos de configuração.

[Elemento **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md) Especifica a política de associação de assembly no nível da configuração.

[Elemento **\<linkedConfiguration>** ](linkedconfiguration-element.md) Especifica um arquivo de configuração a ser incluído.

[Esquema de configurações de inicialização](./startup/index.md) Descreve os elementos que especificam qual versão do Common Language Runtime deve ser usada.

[Esquema de configurações de tempo de execução](./runtime/index.md) Descreve os elementos que configuram o comportamento de associação e do tempo de execução do assembly.

[Esquema de configurações de rede](./network/index.md) Descreve os elementos que especificam como o .NET Framework se conecta à Internet.

[Esquema de configurações de criptografia](./cryptography/index.md) Descreve os elementos que mapeiam nomes de algoritmo amigáveis para classes que implementam algoritmos de criptografia.

[Esquema de seções de configuração](configuration-sections-schema.md) Descreve os elementos usados para criar e usar as seções de configuração para as configurações personalizadas.

[Esquema de configurações de depuração e rastreamento](./trace-debug/index.md) Descreve os elementos que especificam opções de rastreamento e ouvintes.

[Esquema de configurações do compilador e do provedor de linguagem](./compiler/index.md) Descreve os elementos que especificam a configuração do compilador para os provedores de linguagem disponíveis.

[Esquema de configurações do aplicativo](application-settings-schema.md) Descreve os elementos que permitem que um aplicativo do Windows Forms ou do ASP.NET armazene e recupere configurações no escopo do aplicativo e no escopo do usuário.

[Esquema de configurações do aplicativo](./appsettings/index.md) Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.

[Esquema de configurações da Web](./web/index.md) Todos os elementos do esquema de configurações da Web, incluindo elementos para configurar como o ASP.NET funciona com um aplicativo host, como o IIS. Usado em arquivos *Aspnet.config*.

[Esquema de configuração do Windows Forms](winforms/index.md) Todos os elementos na seção de configuração do aplicativo do Windows Forms, incluindo personalizações, como suporte para vários monitores e para alto DPI.

[Esquema de configuração do WCF](./wcf/index.md) Todos os elementos que permitem configurar aplicativos clientes e de serviço do WCF.

[Sintaxe de diretiva do WCF](./wcf-directive/index.md) Descreve a diretiva `@ServiceHost`, que define atributos específicos da página usados pelo compilador .svc.

[Esquema de configuração do WIF](windows-identity-foundation/index.md) Todos os elementos do esquema de configuração do WIF (Windows Identity Foundation).

## <a name="related-sections"></a>Seções relacionadas

[Esquema de configurações remotas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Descreve os elementos que configuram aplicativos clientes e para servidores que implementam a comunicação remota.

[Esquema de configurações do ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Descreve os elementos que controlam o comportamento de aplicativos Web do ASP.NET.

[Esquema de configurações de serviços Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Descreve os elementos que controlam o comportamento dos serviços Web do ASP.NET e de seus clientes.

[Configurando aplicativos do .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Descreve como configurar a segurança, associação de assembly e a comunicação remota no .NET Framework.
