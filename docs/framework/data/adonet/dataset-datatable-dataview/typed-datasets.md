---
title: DataSets tipados
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 7c8111e0e62a57b6745a5ea0387fc65a05839df8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785843"
---
# <a name="typed-datasets"></a>DataSets tipados
Juntamente com acesso de associação tardia por meio de valores com variáveis fracamente tipadas, o <xref:System.Data.DataSet> fornece acesso a dados por meio de uma metáfora fortemente tipada. Tabelas e colunas que fazem parte do **conjunto** de um podem ser acessadas usando nomes amigáveis de usuário e variáveis com rigidez de tipos.  
  
 Um **DataSet** tipado é uma classe derivada de um **DataSet**. Como tal, ele herda todos os métodos, eventos e propriedades de um **conjunto**de uma. Além disso, um **DataSet** tipado fornece métodos, eventos e propriedades com rigidez de tipos. Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção. Além da melhor legibilidade do código, um **DataSet** tipado também permite que o editor de código do Visual Studio .net preencha automaticamente as linhas conforme você digita.  
  
 Além disso, o **conjunto** de texto com rigidez de tipos fornece acesso a valores como o tipo correto no momento da compilação. Com um **conjunto**de texto com rigidez de tipos, erros de tipo incompatíveis são capturados quando o código é compilado em vez de em tempo de execução.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Gerando conjuntos de dados fortemente tipados](generating-strongly-typed-datasets.md)  
 Descreve como criar e usar um conjunto de um **DataSet**com rigidez de tipos.  
  
 [Anotando DataSets tipados](annotating-typed-datasets.md)  
 Descreve como anotar o esquema XSD (linguagem de definição de esquema XML) usado para gerar um **conjunto**de dado com rigidez de tipos, para dar aos elementos do **conjunto** de dado nomes amigáveis sem alterar o esquema subjacente.  
  
## <a name="see-also"></a>Consulte também

- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
