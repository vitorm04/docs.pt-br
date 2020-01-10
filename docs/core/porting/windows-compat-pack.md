---
title: Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core
description: Saiba mais sobre o pacote de compatibilidade do Windows e como você pode usá-lo para portar o código de .NET Framework existente para o .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 65530987a3cded941b6a292118ed9bfdb6f5b86c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715476"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core

Alguns dos problemas mais comuns encontrados ao portar código existente para o .NET Core são dependências de APIs e tecnologias que só são encontradas no .NET Framework. O *Pacote de Compatibilidade do Windows* fornece muitas dessas tecnologias, portanto, é muito mais fácil compilar aplicativos .NET Core e bibliotecas do .NET Standard.

Esse pacote é uma [extensão lógica do .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) que aumenta consideravelmente o conjunto de APIs e o código existente é compilado quase sem modificações. Para manter a promessa do .NET Standard ("é o conjunto de APIs que todas as implementações do .NET fornecem"), o pacote não inclui tecnologias que não funcionam em todas as plataformas, como registro, Instrumentação de Gerenciamento do Windows (WMI) ou emissão de reflexo API.

O pacote de compatibilidade do Windows fica sobre o .NET Standard e fornece acesso a tecnologias que são somente Windows. É especialmente útil para os clientes que desejam migrar para o .NET Core, mas pretendem permanecer no Windows como uma primeira etapa. Nesse cenário, não ser capaz de usar tecnologias somente do Windows é apenas um obstáculo de migração sem benefícios arquitetônicos.

## <a name="package-contents"></a>Conteúdo do pacote

O pacote de compatibilidade do Windows é fornecido por meio do [pacote NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado de projetos direcionados ao .NET Core ou .net Standard.

Ele fornece cerca de 20.000 APIs, incluindo APIs somente Windows, bem como APIs de multiplataforma das seguintes áreas de tecnologia:

- Páginas de código
- CodeDom
- Configuração do
- Serviços de Diretório
- Desenho
- ODBC
- Permissões
- Portas
- ACL (Listas de Controle de Acesso) do Windows
- {1&gt;{2&gt;Windows Communication Foundation (WCF)&lt;2}&lt;1}
- Criptografia do Windows
- EventLog do Windows
- WMI (Instrumentação de Gerenciamento do Windows)
- Contadores de Desempenho do Windows
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
