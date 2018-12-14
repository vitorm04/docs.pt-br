---
title: Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core
description: Saiba mais sobre o Pacote de Compatibilidade do Windows e como você pode usá-lo para portar um código existente do .NET Framework para o .NET Core
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.custom: seodec18
ms.openlocfilehash: 42c2c2a0b9b00436fa5c17d3825c720561b3f122
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144605"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core

Alguns dos problemas mais comuns durante a portabilidade do código existente para o .NET Core são as dependências de APIs e tecnologias encontradas apenas no .NET Framework. O *Pacote de Compatibilidade do Windows* fornece muitas dessas tecnologias, portanto, é muito mais fácil compilar aplicativos .NET Core e bibliotecas do .NET Standard.

Esse pacote é uma [extensão lógica do .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) que aumenta consideravelmente o conjunto de APIs e o código existente é compilado quase sem modificações. No entanto, para manter a promessa do .NET Standard (“é o conjunto de APIs fornecido por todas as implementações do .NET”), isso não inclui tecnologias que não funcionam em todas as plataformas, como o Registro, o WMI (Instrumentação de Gerenciamento do Windows) ou as APIs de emissão de reflexão.

O *Pacote de Compatibilidade do Windows* se baseia no .NET Standard e fornece acesso às tecnologias somente Windows. É especialmente útil para os clientes que desejam migrar para o .NET Core, mas pretendem permanecer no Windows como uma primeira etapa. Nesse cenário, não conseguir usar as tecnologias somente Windows é apenas um obstáculo de migração sem nenhum benefício de arquitetura.

## <a name="package-contents"></a>Conteúdo do pacote

O *Pacote de Compatibilidade do Windows* é fornecido por meio do Pacote NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado em projetos direcionados ao .NET Core ou .NET Standard.

Ele fornece cerca de 20.000 APIs, incluindo APIs somente Windows, bem como APIs de multiplataforma das seguintes áreas de tecnologia:

* Páginas de código
* CodeDom
* Configuração
* Serviços de Diretório
* Desenho
* ODBC
* Permissões
* Portas
* ACL (Listas de Controle de Acesso) do Windows
* Windows Communication Foundation (WCF)
* Criptografia do Windows
* EventLog do Windows
* WMI (Instrumentação de Gerenciamento do Windows)
* Contadores de Desempenho do Windows
* Registro do Windows
* Cache do Windows Runtime
* Serviços Windows

Para obter mais informações, consulte as [especificações do pacote de compatibilidade](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Introdução

1. Antes da portabilidade, examine o [Processo de portabilidade](index.md).

2. Ao portar um código existente para o .NET Core ou .NET Standard, instale o pacote NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Caso deseje permanecer no Windows, você estará pronto.

4. Se desejar executar o aplicativo .NET Core ou a biblioteca .NET Standard no Linux ou macOS, use o [Analisador de API](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) para localizar o uso de APIs que não funcionarão com multiplataforma.

5. Remova os usos dessas APIs, substitua-os por alternativas de multiplataforma ou proteja-os usando uma verificação de plataforma, como:

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

