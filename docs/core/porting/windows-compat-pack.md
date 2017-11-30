---
title: Movimentando para .NET Core - usando o pacote de compatibilidade do Windows
description: "Saiba mais sobre o pacote de compatibilidade do Windows e como você pode usá-lo ao portar código do .NET Framework existente para .NET Core"
keywords: ".NET, o núcleo do .NET, Windows, compatibilidade"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 5094baee77aba4d1e148f807d842a4a2d3405cf7
ms.sourcegitcommit: 86cf9b4c7104485a9870645705b9a1a4b6ca8e2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2017
---
# <a name="using-the-windows-compatibility-pack"></a>Usando o pacote de compatibilidade do Windows

Um dos problemas mais comuns que os desenvolvedores enfrentam ao portar seu código existente para .NET Core é que eles dependem de APIs e tecnologias que existem somente no .NET Framework. O *pacote de compatibilidade do Windows* é fornecer muitas dessas tecnologias para que a criação de aplicativos .NET Core, bem como bibliotecas .NET padrão se torna muito mais viável para o código existente.

Este pacote é uma lógica [extensão do .NET 2.0 padrão](../whats-new/index.md#api-changes-and-library-support) que significativamente o conjunto de APIs aumenta e o código existente compila quase sem modificações. Mas, para manter a promessa de .NET padrão ("é o conjunto de APIs que fornecem todas as implementações de .NET"), isso não inclui tecnologias que não funcionam em todas as plataformas, como o registro, o Windows Management Instrumentation (WMI), ou a emissão de reflexão APIs.

O *pacote de compatibilidade do Windows* assenta sobre .NET padrão e fornece acesso às tecnologias Windows somente. É especialmente útil para os clientes que desejarem mover para o .NET Core, mas plano permaneça no Windows como uma primeira etapa. Nesse cenário, a não ser capaz de usar tecnologias somente do Windows é apenas uma barreira de migração com zero benefícios da arquitetura.

## <a name="package-contents"></a>Conteúdo do pacote

O *pacote de compatibilidade do Windows* é fornecido por meio do pacote do NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado de projetos direcionados .NET Core ou .NET padrão.

Ele fornece cerca de 20.000 APIs, incluindo APIs somente do Windows, bem como entre plataformas de áreas de tecnologia a seguir:

* Páginas de código
* CodeDom
* Configuração
* Serviços de Diretório
* desenho
* ODBC
* Permissões
* Portas
* Listas de controle de acesso (ACL) do Windows
* Windows Communication Foundation (WCF)
* Criptografia do Windows
* Log de eventos do Windows
* WMI (Instrumentação de Gerenciamento do Windows)
* Contadores de desempenho do Windows
* Registro do Windows
* Cache de tempo de execução do Windows
* Serviços Windows

Para obter mais informações, consulte o [especificações do pacote de compatibilidade](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Introdução

1. Antes de portar, certifique-se de examinar o [processo movimentando](index.md).

2. Ao portar código existente para .NET Core ou padrão do .NET, instale o pacote NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Se você deseja manter no Windows, você esteja pronto.

4. Se você quiser executar o aplicativo de núcleo do .NET ou biblioteca .NET padrão em Linux ou macOS, use o [API analisador](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) para localizar o uso de APIs que não funcionará entre plataformas.

5. Remova os usos dessas APIs, substituí-las por alternativas de plataforma cruzada ou protegê-los usando uma verificação de plataforma, como:

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

Para ver uma demonstração, confira o [vídeo do Channel 9 do pacote de compatibilidade do Windows](https://channel9.msdn.com/Events/Connect/2017/T123).

