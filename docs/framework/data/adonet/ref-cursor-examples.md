---
title: Exemplos de REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 00e1cd1b9c13514979ee22b32996d35e1bd1c3e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615342"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="83e2d-102">Exemplos de REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="83e2d-102">REF CURSOR Examples</span></span>
<span data-ttu-id="83e2d-103">Os exemplos de REF CURSOR são compostos dos seguintes três exemplos do Microsoft Visual Basic que demonstram como usar REF CURSORs.</span><span class="sxs-lookup"><span data-stu-id="83e2d-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="83e2d-104">Amostra</span><span class="sxs-lookup"><span data-stu-id="83e2d-104">Sample</span></span>|<span data-ttu-id="83e2d-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="83e2d-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83e2d-106">Parâmetros de REF CURSOR em um OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="83e2d-106">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="83e2d-107">Este exemplo executa um procedimento armazenado PL/SQL, que retorna um parâmetro de REF CURSOR e lê o valor como um <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="83e2d-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="83e2d-108">Recuperando dados de vários REF CURSORs usando um OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="83e2d-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="83e2d-109">Este exemplo executa um procedimento armazenado PL/SQL que retorna dois parâmetros de REF CURSOR e lê os valores usando um **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="83e2d-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="83e2d-110">Preenchendo um DataSet usando um ou mais REF CURSORs</span><span class="sxs-lookup"><span data-stu-id="83e2d-110">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="83e2d-111">Este exemplo executa um procedimento armazenado PL/SQL, que retorna dois parâmetros de REF CURSOR e preenche um <xref:System.Data.DataSet> com as linhas retornadas.</span><span class="sxs-lookup"><span data-stu-id="83e2d-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="83e2d-112">Para usar esses exemplos, você pode precisar criar as tabelas Oracle e deve criar um pacote PL/SQL e o corpo do pacote.</span><span class="sxs-lookup"><span data-stu-id="83e2d-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="83e2d-113">Criando as tabelas do Oracle</span><span class="sxs-lookup"><span data-stu-id="83e2d-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="83e2d-114">Estes exemplos usam as tabelas que são definidas no esquema Scott/Tiger do Oracle.</span><span class="sxs-lookup"><span data-stu-id="83e2d-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="83e2d-115">O esquema Scott/Tiger do Oracle é incluído na maioria das instalações do Oracle.</span><span class="sxs-lookup"><span data-stu-id="83e2d-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="83e2d-116">Se esse esquema não existir, você poderá usar o arquivo de comandos SQL em {OracleHome}\rdbms\admin\scott.sql para criar as tabelas e os índices usados por esses exemplos.</span><span class="sxs-lookup"><span data-stu-id="83e2d-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="83e2d-117">Criando o pacote Oracle e o corpo do pacote</span><span class="sxs-lookup"><span data-stu-id="83e2d-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="83e2d-118">Esses exemplos requerem o seguinte pacote PL/SQL e o corpo do pacote no seu servidor.</span><span class="sxs-lookup"><span data-stu-id="83e2d-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="83e2d-119">Crie o seguinte pacote Oracle no servidor Oracle.</span><span class="sxs-lookup"><span data-stu-id="83e2d-119">Create the following Oracle package on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 <span data-ttu-id="83e2d-120">Crie o seguinte corpo do pacote Oracle no servidor Oracle.</span><span class="sxs-lookup"><span data-stu-id="83e2d-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a><span data-ttu-id="83e2d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83e2d-121">See also</span></span>
- [<span data-ttu-id="83e2d-122">REF CURSORs do Oracle</span><span class="sxs-lookup"><span data-stu-id="83e2d-122">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)
- <span data-ttu-id="83e2d-123">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="83e2d-123">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
