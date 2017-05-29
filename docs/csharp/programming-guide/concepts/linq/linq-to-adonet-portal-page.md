---
title: "LINQ to ADO.NET (Página do Portal) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 34ffcb1c75daa403388b8708dc7abb0e8c1a370e
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (página do portal)
O [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] permite que você realize consultas em qualquer objeto enumerável em [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] usando o modelo de programação [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].  
  
> [!NOTE]
>  A documentação do [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] está localizada na seção ADO.NET do SDK do .NET Framework: [LINQ e o ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).  
  
 Há três tecnologias separadas do [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] do ADO.NET: [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] e [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]. O [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] fornece consultas mais sofisticadas e otimizadas sobre o <xref:System.Data.DataSet>, o [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] permite que você consulte diretamente esquemas de banco de dados do [!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)] e o [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] permite que você consulte um [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O <xref:System.Data.DataSet> é um dos componentes mais amplamente usados em [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] e é um elemento fundamental do modelo de programação desconectada no qual o [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] se baseia. No entanto, apesar dessa importância, o <xref:System.Data.DataSet> limitou os recursos de consulta.  
  
 O [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] permite que você crie mais recursos sofisticados de consulta no <xref:System.Data.DataSet> usando a mesma funcionalidade de consulta que está disponível para muitas outras fontes de dados.  
  
 Para obter mais informações, consulte [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 O [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] fornece uma infraestrutura em tempo de execução para gerenciar dados relacionais como objetos. No [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], o modelo de dados de um banco de dados relacional é mapeado para um modelo de objeto expresso na linguagem de programação do desenvolvedor. Quando você executa o aplicativo, o [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] converte consultas integradas da linguagem no modelo de objeto no SQL e as envia para o banco de dados para execução. Quando o banco de dados retorna os resultados, o [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] os converte em objetos que podem ser manipulados.  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] inclui suporte para procedimentos armazenados e funções definidas pelo usuário no banco de dados e para herança no modelo de objeto.  
  
 Para obter mais informações, consulte [LINQ to SQL](https://msdn.microsoft.com/library/bb386976).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Por meio do [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)], os dados relacionais são expostos como objetos no ambiente .NET. Isso torna a camada do objeto um destino ideal para o suporte do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] permitindo que os desenvolvedores formulem consultas no banco de dados na linguagem usada para criar a lógica de negócios. Esse recurso é conhecido como [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]. Consulte [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) para obter mais informações.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ e o ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)   
 [LINQ (Consulta Integrada à Linguagem) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
