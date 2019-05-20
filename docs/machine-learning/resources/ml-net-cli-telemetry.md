---
title: Coleta de telemetria pela CLI do ML.NET
description: Conheça os recursos de telemetria da CLI do ML.NET que coletam informações de uso para análise, quais dados são coletados e como desabilitá-los. Além disso, encontre links para o contrato de licença do .NET e informações sobre a conformidade com o RGPD da Microsoft.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 49ebd6c9e1b77c85d891b8c9fb8cbd5c66b478a9
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065539"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Coleta de telemetria pela CLI do ML.NET

A [CLI do ML.NET](http://aka.ms/mlnet-cli) inclui um recurso de telemetria que coleta dados anônimos de uso que são agregados para uso pela Microsoft.

## <a name="how-microsoft-uses-the-data"></a>Como a Microsoft usa os dados

A equipe de produto usa dados de telemetria do ML.NET CLI para ajudar a entender como melhorar as ferramentas. Por exemplo, se os clientes usarem com pouca frequência uma determinada tarefa de aprendizado de máquina, a equipe de produto investigará por que e usará as descobertas para priorizar o desenvolvimento de recursos. A telemetria da CLI do ML.NET também ajuda com a depuração de problemas, como falhas e anomalias de código. 

Embora a equipe de produto aprecia essas informações, ela também sabe que nem todo mundo deseja enviá-las. [Saiba como desabilitar a telemetria.](#opt-out-of-data-collection)

## <a name="scope"></a>Escopo

O comando `mlnet` inicia a CLI do ML.NET, mas o comando em si não coleta telemetria.

A telemetria *não está habilitada* quando você executa o `mlnet` sem outro comando anexado. Por exemplo:

- `mlnet`
- `mlnet --help`

A telemetria *está habilitado* quando você executa um [comando da CLI do ML.NET](../reference/ml-net-cli-reference.md), como `mlnet auto-train`.

## <a name="opt-out-of-data-collection"></a>Recusar a coleta de dados

O recurso de telemetria da CLI do ML.NET Core está habilitado por padrão.

Recuse o recurso de telemetria configurando a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`. Essa variável de ambiente se aplica globalmente à ferramenta de CLI do .NET.

## <a name="data-points-collected"></a>Pontos de dados coletados

O recurso coleta os seguintes dados:

- Quais comandos são invocados, como `auto-train`
- Endereço MAC com hash: uma ID única e criptograficamente anônima (SHA256) para um computador
- Carimbo de data/hora de uma invocação
- Três endereços IP de octeto usados para determinar a localização geográfica
- Nome de todos os argumentos/parâmetros usados. Não valores do cliente, como cadeias de caracteres
- Sistema operacional e versão
- Valor do parâmetro --ml-task: Valores categóricos, como `regression`, `binary-classification` e `multiclass-classification`
- Tamanho do arquivo do conjunto de dados [logarítmicos arredondados](https://en.wikipedia.org/wiki/Rounding#Rounding_to_a_specified_power) (mais próximo da potência de 2)
- `ExitCode` do comando

Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Azure Application Insights](https://azure.microsoft.com/services/application-insights/), mantidos em acesso restrito e usados sob controles de segurança rigorosos dos sistemas do [Armazenamento do Microsoft Azure](https://azure.microsoft.com/services/storage/) seguros.

### <a name="data-points-not-collected"></a>Pontos de dados não coletados
O recurso de telemetria *não* coleta:
- dados pessoais, como nomes de usuário
- nomes de arquivo de conjunto de dados
- dados de arquivos de conjunto de dados

Se você suspeita que a telemetria da CLI do ML.NET está coletando dados confidenciais ou que os dados estão sendo manipulados de modo inseguro ou inadequado, registre um problema no repositório [ML.NET](https://github.com/dotnet/machinelearning) para investigação.

## <a name="license"></a>Licença

A distribuição da Microsoft da CLI do ML.NET é licenciada com os [Termos de licença de software da Microsoft: Biblioteca do Microsoft .NET](https://aka.ms/dotnet-core-eula). Para obter detalhes sobre a coleta e o processamento de dados, veja a seção intitulada "Dados".

## <a name="disclosure"></a>Divulgação

Quando você executar pela primeira vez um [comando da CLI do ML.NET](../reference/ml-net-cli-reference.md), como `mlnet auto-train`, a ferramenta da CLI do ML.NET exibe o texto de divulgação que informa como recusar a telemetria. O texto pode variar um pouco dependendo da versão da CLI que você está executando.

## <a name="see-also"></a>Consulte também
- [Referência da CLI do ML.NET](../reference/ml-net-cli-reference.md)
- [Termos de licença de software da Microsoft: Microsoft do Microsoft .NET](https://aka.ms/dotnet-core-eula)
- [Privacidade na Microsoft](https://www.microsoft.com/en-us/trustcenter/privacy/)
- [Política de privacidade da Microsoft](https://privacy.microsoft.com/en-us/privacystatement)
