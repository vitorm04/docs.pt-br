---
title: Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core
description: Saiba mais sobre o pacote de compatibilidade do Windows e como você pode usá-lo para portar o código de .NET Framework existente para o .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733615"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core

Alguns dos problemas mais comuns encontrados ao portar código existente para o .NET Core são dependências de APIs e tecnologias que só são encontradas no .NET Framework. O *Pacote de Compatibilidade do Windows* fornece muitas dessas tecnologias, portanto, é muito mais fácil compilar aplicativos .NET Core e bibliotecas do .NET Standard.

O Compatibility Pack é uma [extensão lógica do .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) que aumenta significativamente o conjunto de APIs. O código existente é compilado com quase nenhuma modificação. Para manter sua promessa de "o conjunto de APIs que todas as implementações do .NET fornecem", .NET Standard não inclui tecnologias que não funcionam em todas as plataformas, como registro, Instrumentação de Gerenciamento do Windows (WMI) ou APIs de emissão de reflexo. O pacote de compatibilidade do Windows fica sobre o .NET Standard e fornece acesso a essas tecnologias somente do Windows. Ele é especialmente útil para clientes que desejam migrar para o .NET Core, mas planejam permanecer no Windows, pelo menos como uma primeira etapa. Nesse cenário, ser capaz de usar tecnologias somente do Windows elimina o obstáculo de migração.

## <a name="package-contents"></a>Conteúdo do pacote

O pacote de compatibilidade do Windows é fornecido por meio do [pacote NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado de projetos direcionados ao .NET Core ou .net Standard.

Ele fornece cerca de 20.000 APIs, incluindo APIs somente Windows, bem como APIs de multiplataforma das seguintes áreas de tecnologia:

- Páginas de código
- CodeDom
- Configuração
- Serviços de Diretório
- Desenho
- ODBCODBC
- Permissões
- Portas
- ACL (Listas de Controle de Acesso) do Windows
- Windows Communication Foundation (WCF)
- Criptografia do Windows
- EventLog do Windows
- WMI (Instrumentação de Gerenciamento do Windows)
- Contadores de desempenho do Windows
- Registro do Windows
- Cache do Windows Runtime
- Serviços do Windows

Para obter mais informações, confira a [especificação do pacote de compatibilidade](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Introdução

1. Antes de portar, certifique-se de dar uma olhada no [processo de portabilidade](index.md).

2. Ao portar código existente para .NET Core ou .NET Standard, instale o [pacote NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Caso deseje permanecer no Windows, você estará pronto.

3. Se desejar executar o aplicativo .NET Core ou a biblioteca .NET Standard no Linux ou macOS, use o [Analisador de API](../../standard/analyzers/api-analyzer.md) para localizar o uso de APIs que não funcionarão com multiplataforma.

4. Remova os usos dessas APIs, substitua-os por alternativas de multiplataforma ou proteja-os usando uma verificação de plataforma, como:

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

Para ver uma demonstração, confira o [vídeo do Channel 9 sobre o Pacote de Compatibilidade do Windows](https://channel9.msdn.com/Events/Connect/2017/T123).
