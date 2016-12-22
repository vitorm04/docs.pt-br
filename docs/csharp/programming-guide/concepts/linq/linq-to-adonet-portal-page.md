---
title: "LINQ to ADO.NET (p&#225;gina do portal) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ to ADO.NET (p&#225;gina do portal)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] permite que você consultar sobre qualquer objeto enumerável em [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] usando o [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] modelo de programação.  
  
> [!NOTE]
>  O [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] documentação está localizada na seção ADO.NET do SDK do .NET Framework: [LINQ e o ADO.NET](../Topic/LINQ%20and%20ADO.NET.md).  
  
 Há três ADO.NET separada [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] tecnologias: [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], e [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)].[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] fornece a consulta mais sofisticada e otimizada sobre o <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] permite consultar diretamente [!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)] esquemas de banco de dados e [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] permite que você consulte um [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)].  
  
## LINQ to DataSet  
 O <xref:System.Data.DataSet> é um dos componentes mais amplamente usados no [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)], e é um elemento fundamental da programação desconectado de modelo que [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] se baseia. Apesar dessa importância, no entanto, o <xref:System.Data.DataSet> tem recursos de consulta limitados.  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] permite que você crie recursos sofisticados de consulta em <xref:System.Data.DataSet> usando a mesma funcionalidade de consulta está disponível para muitas outras fontes de dados.  
  
 Para obter mais informações, consulte [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] Fornece uma infra\-estrutura de tempo de execução para gerenciar dados relacionais como objetos. Em [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], o modelo de dados de um banco de dados relacional é mapeado para um modelo de objeto expressado na linguagem de programação do desenvolvedor. Quando você executar o aplicativo, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] converte consultas integradas à linguagem no modelo de objeto em SQL e as envia para o banco de dados para execução. Quando o banco de dados retorna os resultados, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] converte\-os novamente em objetos que você pode manipular.  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] inclui suporte para procedimentos armazenados e funções definidas pelo usuário no banco de dados e também para herança no modelo de objeto.  
  
 Para obter mais informações, consulte [LINQ to SQL](../Topic/LINQ%20to%20SQL.md).  
  
## LINQ to Entities  
 Por meio de [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)], dados relacionais são expostos como objetos no ambiente .NET. Isso faz com que o objeto de camada a um destino ideal para [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] suporte, permitindo que os desenvolvedores formulem consultas no banco de dados do idioma usado para criar a lógica de negócios. Esse recurso é conhecido como [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]. Consulte [LINQ to Entities](../Topic/LINQ%20to%20Entities.md) para obter mais informações.  
  
## Consulte também  
 [LINQ e o ADO.NET](../Topic/LINQ%20and%20ADO.NET.md)   
 [Consulta integrada à linguagem \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/index.md)