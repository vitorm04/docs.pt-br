---
title: REF CURSORs do Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f01ace7bc7dfe1191dac8990210032b60e16f255
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="49926-102">REF CURSORs do Oracle</span><span class="sxs-lookup"><span data-stu-id="49926-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="49926-103">O provedor de dados .NET Framework para Oracle oferece suporte a Oracle **REF CURSOR** tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="49926-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="49926-104">Ao usar o provedor de dados para trabalhar com REF CURSORs do Oracle, você deve considerar os seguintes comportamentos.</span><span class="sxs-lookup"><span data-stu-id="49926-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49926-105">Alguns comportamentos diferem dos do Provedor OLE DB para Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="49926-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="49926-106">Por motivos de desempenho, o provedor de dados para Oracle não automaticamente associa **REF CURSOR** tipos de dados, como o MSDAORA, a menos que você especifique explicitamente.</span><span class="sxs-lookup"><span data-stu-id="49926-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="49926-107">O provedor de dados não oferece suporte a nenhuma sequência de escape de ODBC, incluindo o escape {resultset} usado para especificar parâmetros de REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="49926-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="49926-108">Para executar um procedimento armazenado que retorna os cursores de referência, você deve definir os parâmetros de <xref:System.Data.OracleClient.OracleParameterCollection> com um <xref:System.Data.OracleClient.OracleType> de **Cursor** e um <xref:System.Data.OracleClient.OracleParameter.Direction%2A> de **saída**.</span><span class="sxs-lookup"><span data-stu-id="49926-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="49926-109">O provedor de dados oferece suporte a REF CURSORs de associação como parâmetros de saída somente.</span><span class="sxs-lookup"><span data-stu-id="49926-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="49926-110">O provedor não oferece suporte a REF CURSORs como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="49926-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="49926-111">A obtenção de <xref:System.Data.OracleClient.OracleDataReader> do valor do parâmetro não é suportada.</span><span class="sxs-lookup"><span data-stu-id="49926-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="49926-112">Os valores são do tipo <xref:System.DBNull> após a execução do comando.</span><span class="sxs-lookup"><span data-stu-id="49926-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="49926-113">A única **CommandBehavior** valor de enumeração que funciona com cursores de referência (por exemplo, ao chamar <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) é **CloseConnection**; todos os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="49926-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="49926-114">A ordem dos cursores REF o **OracleDataReader** depende da ordem de parâmetros no **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="49926-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="49926-115">A propriedade <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> é ignorada.</span><span class="sxs-lookup"><span data-stu-id="49926-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="49926-116">PL/SQL **tabela** não há suporte para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="49926-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="49926-117">No entanto, REF CURSORs são mais eficientes.</span><span class="sxs-lookup"><span data-stu-id="49926-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="49926-118">Se você deve usar um **tabela** tipo de dados, use o provedor OLE DB .NET dados com MSDAORA.</span><span class="sxs-lookup"><span data-stu-id="49926-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49926-119">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="49926-119">In This Section</span></span>  
 [<span data-ttu-id="49926-120">Exemplos de REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="49926-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="49926-121">Contém três exemplos que demonstram como usar REF CURSORs.</span><span class="sxs-lookup"><span data-stu-id="49926-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="49926-122">Parâmetros de REF CURSOR em um OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="49926-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="49926-123">Demonstra como executar um procedimento armazenado PL/SQL que retorna um parâmetro REF CURSOR e lê o valor como um **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="49926-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="49926-124">Recuperando dados de vários REF CURSORs usando um OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="49926-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="49926-125">Demonstra como executar um procedimento armazenado PL/SQL que retorna dois parâmetros REF CURSOR e lê os valores usando um **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="49926-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="49926-126">Preenchendo um DataSet usando um ou mais REF CURSORs</span><span class="sxs-lookup"><span data-stu-id="49926-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="49926-127">Demonstra como executar um procedimento armazenado PL/SQL, que retorna dois parâmetros de REF CURSOR e preenche um <xref:System.Data.DataSet> com as linhas retornadas.</span><span class="sxs-lookup"><span data-stu-id="49926-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49926-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49926-128">See Also</span></span>  
 <span data-ttu-id="49926-129">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="49926-129">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>  
 <span data-ttu-id="49926-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="49926-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
