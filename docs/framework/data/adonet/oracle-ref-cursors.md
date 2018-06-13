---
title: REF CURSORs do Oracle
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7aae9b2e4b39cf164a93ba82212b5705f583d761
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758718"
---
# <a name="oracle-ref-cursors"></a>REF CURSORs do Oracle
O provedor de dados .NET Framework para Oracle oferece suporte a Oracle **REF CURSOR** tipo de dados. Ao usar o provedor de dados para trabalhar com REF CURSORs do Oracle, você deve considerar os seguintes comportamentos.  
  
> [!NOTE]
>  Alguns comportamentos diferem dos do Provedor OLE DB para Oracle (MSDAORA).  
  
-   Por motivos de desempenho, o provedor de dados para Oracle não automaticamente associa **REF CURSOR** tipos de dados, como o MSDAORA, a menos que você especifique explicitamente.  
  
-   O provedor de dados não oferece suporte a nenhuma sequência de escape de ODBC, incluindo o escape {resultset} usado para especificar parâmetros de REF CURSOR.  
  
-   Para executar um procedimento armazenado que retorna os cursores de referência, você deve definir os parâmetros de <xref:System.Data.OracleClient.OracleParameterCollection> com um <xref:System.Data.OracleClient.OracleType> de **Cursor** e um <xref:System.Data.OracleClient.OracleParameter.Direction%2A> de **saída**. O provedor de dados oferece suporte a REF CURSORs de associação como parâmetros de saída somente. O provedor não oferece suporte a REF CURSORs como parâmetros de entrada.  
  
-   A obtenção de <xref:System.Data.OracleClient.OracleDataReader> do valor do parâmetro não é suportada. Os valores são do tipo <xref:System.DBNull> após a execução do comando.  
  
-   A única **CommandBehavior** valor de enumeração que funciona com cursores de referência (por exemplo, ao chamar <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) é **CloseConnection**; todos os outros são ignorados.  
  
-   A ordem dos cursores REF o **OracleDataReader** depende da ordem de parâmetros no **OracleParameterCollection**. A propriedade <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> é ignorada.  
  
-   PL/SQL **tabela** não há suporte para o tipo de dados. No entanto, REF CURSORs são mais eficientes. Se você deve usar um **tabela** tipo de dados, use o provedor OLE DB .NET dados com MSDAORA.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exemplos de REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Contém três exemplos que demonstram como usar REF CURSORs.  
  
 [Parâmetros de REF CURSOR em um OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Demonstra como executar um procedimento armazenado PL/SQL que retorna um parâmetro REF CURSOR e lê o valor como um **OracleDataReader**.  
  
 [Recuperando dados de vários REF CURSORs usando um OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Demonstra como executar um procedimento armazenado PL/SQL que retorna dois parâmetros REF CURSOR e lê os valores usando um **OracleDataReader**.  
  
 [Preenchendo um DataSet usando um ou mais REF CURSORs](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Demonstra como executar um procedimento armazenado PL/SQL, que retorna dois parâmetros de REF CURSOR e preenche um <xref:System.Data.DataSet> com as linhas retornadas.  
  
## <a name="see-also"></a>Consulte também  
 [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
