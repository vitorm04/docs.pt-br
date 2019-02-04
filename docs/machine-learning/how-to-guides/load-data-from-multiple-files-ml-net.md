---
title: Carregar dados de vários arquivos para o processamento do aprendizado de máquina – ML.NET
description: Saiba como carregar dados de vários arquivos a serem usados para criar, treinar e pontuar um modelo de machine learning com o ML.NET
ms.date: 01/29/2019
ms.custom: mvc,how-to
ms.openlocfilehash: fe6758e46d923dc07908e1334056ea8394c1085e
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479978"
---
# <a name="load-data-from-multiple-files-for-machine-learning-processing---mlnet"></a>Carregar dados de vários arquivos para o processamento do aprendizado de máquina – ML.NET

Use o `TextLoader` e especifique uma matriz de arquivos para o método `Read`. Os arquivos precisam ter o mesmo esquema (mesmo número e tipo de colunas):

* [Arquivo de exemplo 1](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.train)
* [Arquivo de exemplo 2](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.test)

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

// Now read the files (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(exampleFile1, exampleFile2);
```