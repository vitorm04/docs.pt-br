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
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039154"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Esquema de arquivos de configuração para o .NET Framework

Arquivos de configuração são arquivos XML padrão que você pode usar para alterar as configurações e definir diretivas para seus aplicativos. O esquema de configuração do .NET Framework consiste em elementos que você pode usar em arquivos de configuração para controlar o comportamento de seus aplicativos. O sumário desta seção reflete a hierarquia de esquema para inicialização, runtime, rede e outros tipos de configuração.

Para obter informações sobre os tipos, o formato e o local dos arquivos de configuração, consulte [configurar aplicativos](../index.md). Familiarize-se com XML para editar os arquivos de configuração diretamente.

> [!IMPORTANT]
> Os atributos e as marcas XML em arquivos de configuração diferenciam maiúsculas de minúsculas.

## <a name="in-this-section"></a>Nesta seção

[ **\<** elemento de > de configuração](configuration-element.md)\
O elemento de nível superior para todos os arquivos de configuração.

[ **\<o elemento > assembly** ](assemblybinding-element-for-configuration.md)\
Especifica a diretiva de ligação de assembly no nível de configuração.

[ **\<elemento de > linkedConfiguration** ](linkedconfiguration-element.md)\
Especifica um arquivo de configuração a ser incluído.

\ de [esquema das configurações de inicialização](./startup/index.md)
Elementos que especificam qual versão do Common Language Runtime usar.

\ de [esquema de configurações de tempo de execução](./runtime/index.md)
Elementos que configuram Associação de assembly e comportamento de tempo de execução.

[Esquema de configurações de rede](./network/index.md)\
Elementos que especificam como o .NET Framework se conecta à Internet.

\ de [esquema de configurações de criptografia](./cryptography/index.md)
Elementos que mapeiam nomes de algoritmos amigáveis para classes que implementam algoritmos de criptografia.

\ de [esquema das seções de configuração](configuration-sections-schema.md)
Elementos usados para criar e usar seções de configuração para configurações personalizadas.

\ [de esquema de configurações de rastreamento e depuração](./trace-debug/index.md)
Elementos que especificam opções de rastreamento e ouvintes.

\ [de esquema de configurações do provedor de idiomas e do compilador](./compiler/index.md)
Elementos que especificam a configuração do compilador para provedores de idiomas disponíveis.

\ de [esquema de configurações do aplicativo](application-settings-schema.md)
Elementos que permitem a um aplicativo Windows Forms ou ASP.NET armazenar e recuperar configurações no escopo do aplicativo e no escopo do usuário.

\ de [esquema de configurações do aplicativo](./appsettings/index.md)
Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.

\ de [esquema de configurações da Web](./web/index.md)
Elementos para configurar como o ASP.NET funciona com um aplicativo host como o IIS. Usado em arquivos *Aspnet.config*.

\ [esquema de configuração do Windows Forms](winforms/index.md)
Todos os elementos na seção de configuração Windows Forms aplicativo, que inclui personalizações, como suporte a vários monitores e alto DPI.

\ de [esquema de configuração do WCF](./wcf/index.md)
Todos os elementos que permitem que você configure aplicativos cliente e serviço WCF.

\ de [sintaxe de diretiva WCF](./wcf-directive/index.md)
Descreve a diretiva `@ServiceHost`, que define os atributos específicos da página usados pelo compilador. svc.

[Esquema de configuração do WIF](windows-identity-foundation/index.md)\
Todos os elementos do esquema de configuração do Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Seções relacionadas

\ de [esquema de configurações de comunicação remota](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))
Descreve os elementos que configuram aplicativos cliente e servidor que implementam a comunicação remota.

\ de [esquema de configurações de ASP.net](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))
Descreve os elementos que controlam o comportamento de aplicativos da Web ASP.NET.

\ de [esquema de configurações de serviços Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))
Descreve os elementos que controlam o comportamento de serviços da Web ASP.NET e de seus clientes.

[Configurando aplicativos .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
Descreve como configurar a segurança, ligação de assembly e comunicação remota do .NET Framework.
