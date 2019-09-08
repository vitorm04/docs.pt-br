---
title: Usando XML em um DataSet
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: ca04f524685e080be6af12a4df6eda585a908683
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784259"
---
# <a name="using-xml-in-a-dataset"></a>Usando XML em um DataSet
Com o ADO.NET, você pode preencher um <xref:System.Data.DataSet> de um fluxo XML ou documento. Você pode usar o fluxo XML ou o documento para fornecer ao <xref:System.Data.DataSet> os dados, as informações de esquema ou ambos. As informações fornecidas do fluxo XML ou documento podem ser combinadas com os dados existentes ou informações do esquema presentes no <xref:System.Data.DataSet>.  
  
 O ADO.NET também permite criar uma representação XML de um <xref:System.Data.DataSet>, com ou sem o esquema, para transportar o <xref:System.Data.DataSet> por HTTP para ser usado por outro aplicativo ou plataforma habilitada para XML. Em uma representação de um <xref:System.Data.DataSet>, os dados são gravados em XML e o esquema, se estiver embutido na representação, é escrito usando a linguagem XSD. O XML e o esquema XML fornecem um formato conveniente para transferir o conteúdo de um <xref:System.Data.DataSet> para e de clientes remotos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [DiffGrams](diffgrams.md)  
 Fornece detalhes sobre o DiffGram, um formato XML usado para ler e gravar o conteúdo de um <xref:System.Data.DataSet>.  
  
 [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)  
 Discute as diferentes opções a serem consideradas ao carregar o conteúdo de um <xref:System.Data.DataSet> de um documento XML.  
  
 [Gravar o conteúdo do conjunto de dados como dados XML](writing-dataset-contents-as-xml-data.md)  
 Descreve como gerar o conteúdo de um <xref:System.Data.DataSet> como dados XML e as diferentes opções de formato XML que você pode usar.  
  
 [Carregando informações de esquema de conjunto de dados de XML](loading-dataset-schema-information-from-xml.md)  
 Discute os métodos <xref:System.Data.DataSet> usados para carregar o esquema de um <xref:System.Data.DataSet> do XML.  
  
 [Gravando informações de esquema de conjunto de dados como XSD](writing-dataset-schema-information-as-xsd.md)  
 Discute os usos para um esquema XML e como gerar um de um <xref:System.Data.DataSet>.  
  
 [Sincronização de DataSet e XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)  
 Descreve o recurso disponível no .NET Framework de acesso síncrono para as exibições relacionais e hierárquicas de um único conjunto de dados, e mostra como criar uma relação síncrona entre um <xref:System.Data.DataSet> e um <xref:System.Xml.XmlDataDocument>.  
  
 [Aninhamento de DataRelations](nesting-datarelations.md)  
 Descreve a importância de objetos <xref:System.Data.DataRelation> aninhados ao representar o conteúdo de um <xref:System.Data.DataSet> como dados XML e descreve como criá-los.  
  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional ou o esquema de um <xref:System.Data.DataSet>, que é criado a partir do esquema XML.  
  
 [Derivando a estrutura relacional do DataSet do esquema XML](inferring-dataset-relational-structure-from-xml.md)  
 Descreve a estrutura relacional ou o esquema resultante de um <xref:System.Data.DataSet>, criado quando é inferido de elementos XML.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)  
 Descreve a arquitetura e os componentes do ADO.NET, e como usá-los para acessar fontes de dados existentes assim como para gerenciar dados de aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
