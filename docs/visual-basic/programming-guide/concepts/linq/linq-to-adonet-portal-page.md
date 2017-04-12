---
title: "LINQ to ADO.NET (Portal de página) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5c71b304dbff960320b1a9f46e38259705b8dadc
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (página do portal)
[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]permite que você consultar sobre qualquer objeto enumerável em [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] usando o [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] modelo de programação.  
  
> [!NOTE]
>  O [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] documentação está localizada na seção ADO.NET do SDK do .NET Framework: [LINQ e o ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).  
  
 Há três tecnologias separadas do [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] do ADO.NET: [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] e [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]. [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]fornece a consulta mais sofisticada e otimizada sobre o <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] permite consultar diretamente [!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)] esquemas de banco de dados e [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] permite que você consulte um [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)].</xref:System.Data.DataSet>  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O <xref:System.Data.DataSet>é um dos componentes mais amplamente usados em [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)], e é um elemento fundamental da programação desconectado de modelo que [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] baseia.</xref:System.Data.DataSet> Apesar dessa importância, no entanto, o <xref:System.Data.DataSet>tem recursos de consulta limitados.</xref:System.Data.DataSet>  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]permite que você crie recursos sofisticados de consulta em <xref:System.Data.DataSet>usando a mesma funcionalidade de consulta está disponível para muitas outras fontes de dados.</xref:System.Data.DataSet>  
  
 Para obter mais informações, consulte [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]Fornece uma infra-estrutura de tempo de execução para gerenciar dados relacionais como objetos. Em [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], o modelo de dados de um banco de dados relacional é mapeado para um modelo de objeto expressado na linguagem de programação do desenvolvedor. Quando você executar o aplicativo, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] converte consultas integradas à linguagem no modelo de objeto em SQL e as envia para o banco de dados para execução. Quando o banco de dados retorna os resultados, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] converte-os novamente em objetos que você pode manipular.  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]inclui suporte para procedimentos armazenados e funções definidas pelo usuário no banco de dados e também para herança no modelo de objeto.  
  
 Para obter mais informações, consulte [LINQ to SQL](https://msdn.microsoft.com/library/bb386976).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Por meio do [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)], os dados relacionais são expostos como objetos no ambiente .NET. Isso torna a camada do objeto um destino ideal para o suporte do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] permitindo que os desenvolvedores formulem consultas no banco de dados na linguagem usada para criar a lógica de negócios. Esse recurso é conhecido como [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]. Consulte [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) para obter mais informações.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ e o ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)   
 [Consulta integrada à linguagem (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
