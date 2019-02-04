---
title: Carregar dados de um arquivo de texto para o processamento do aprendizado de máquina – ML.NET
description: Descubra como carregar dados de um arquivo de texto para ser usado para criar, treinar e pontuar um modelo de aprendizado de máquina com o ML.NET
ms.date: 01/29/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 6a8f74cc5324050ca94e60592f083c35afc68377
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479666"
---
# <a name="load-data-from-a-text-file-for-machine-learning-processing---mlnet"></a>Carregar dados de um arquivo de texto para o processamento do aprendizado de máquina – ML.NET

`TextLoader` é usado para carregar dados de arquivos de texto. Você precisa especificar as colunas de dados, seus tipos e sua localização no arquivo de texto.

Observe que é perfeitamente aceitável ler algumas colunas de um arquivo ou ler a mesma coluna várias vezes.

[Arquivo de exemplo](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):

```console
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse
```

Para carregar os dados de um arquivo de texto:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
    columns: new TextLoader.Column[]
    {
        // A boolean column depicting the 'target label'.
        new TextLoader.Column("IsOver50k",DataKind.BL,0),
        // Three text columns.
        new TextLoader.Column("WorkClass",DataKind.TX,1),
        new TextLoader.Column("Education",DataKind.TX,2),
        new TextLoader.Column("MaritalStatus",DataKind.TX,3)
    },
    hasHeader: true
);

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```