---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 4553be9eeab8792197503d0b1de872f4494277b6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634614"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é um componente do .NET Framework versão 3,5 que fornece uma infraestrutura de tempo de execução para o gerenciamento de dados relacionais como objetos.  
  
> [!NOTE]
> Os dados relacionais aparecem como uma coleção de tabelas bidimensionais (*relações* ou *arquivos simples*), em que as colunas comuns relacionam as tabelas entre si. Para usar o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efetivamente, você deve ter alguma familiaridade com os conceitos fundamentais de bancos de dados relacionais.  
  
 No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o modelo de dados de um banco de dados relacional é mapeado para um modelo de objeto expresso na linguagem de programação do desenvolvedor. Quando o aplicativo é executado, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte em SQL as consultas integradas à linguagem no modelo de objeto e as envia ao banco de dados para execução. Quando o banco de dados retorna os resultados, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte-os novamente em objetos com os quais você pode trabalhar em sua própria linguagem de programação.  
  
 Os desenvolvedores que usam o Visual Studio normalmente usam o Object Relational Designer, que fornece uma interface do usuário para implementar muitos dos recursos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 A documentação incluída nessa versão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] descreve as técnicas, os processos e os blocos de construção básicos necessários para compilar aplicativos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Você também pode pesquisar Microsoft Docs problemas específicos e pode participar do [Fórum do LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), no qual você pode discutir tópicos mais complexos em detalhes com especialistas. Por fim, a [LINQ to SQL: consulta integrada à linguagem .net para dados relacionais](https://go.microsoft.com/fwlink/?LinkId=93205) White Paper detalhes de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tecnologia, completo com C# Visual Basic e exemplos de código.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](getting-started.md)  
 Fornece uma visão concentrada do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] juntamente com informações sobre como começar a usar o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Guia de Programação](programming-guide.md)  
 Fornece etapas para operações de mapeamento, atualização, depuração e tarefas semelhantes.  
  
 [Referência](reference.md)  
 Especifica informações de referência sobre vários aspectos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Os tópicos incluem o mapeamento de tipos SQL-CLR, conversão padrão de operadores de consulta e muito mais.  
  
 [Amostras](samples.md)  
 Fornece links para Visual Basic e C# exemplos.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [LINQ (consulta integrada à linguagem)- C# ](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Fornece visões gerais de tecnologias LINQ no C#.
 
 [LINQ (consulta integrada à linguagem) – Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fornece visões gerais das tecnologias do LINQ no Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Descreve as tecnologias do LINQ para Visual Basic usuários.  
  
 [LINQ e ADO.NET](../../linq-and-ado-net.md)  
 Links para o portal do ADO.NET.  
  
 [LINQ to SQL Walkthroughs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90)) (Passo a passo do LINQ to SQL)  
 Lista tutoriais disponíveis para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)  
 Descreve como baixar bancos de dados de exemplo usados na documentação.  
  
 [Visão geral do controle de servidor Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Descreve como o controle de <xref:System.Web.UI.WebControls.LinqDataSource> expõe consulta integrada à linguagem (LINQ) para desenvolvedores da Web por meio da arquitetura de controle de fonte de dados ASP.NET.
