---
title: Exemplos de REF CURSOR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9d282aba600d2475594887844ef19fc8eea374f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="ref-cursor-examples"></a>Exemplos de REF CURSOR
Os exemplos de REF CURSOR são compostos dos seguintes três exemplos do Microsoft Visual Basic que demonstram como usar REF CURSORs.  
  
|Amostra|Descrição|  
|------------|-----------------|  
|[Parâmetros de REF CURSOR em um OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|Este exemplo executa um procedimento armazenado PL/SQL, que retorna um parâmetro de REF CURSOR e lê o valor como um <xref:System.Data.OracleClient.OracleDataReader>.|  
|[Recuperando dados de vários REF CURSORs usando um OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|Este exemplo executa um procedimento armazenado PL/SQL que retorna dois parâmetros REF CURSOR e lê os valores usando um **OracleDataReader**.|  
|[Preenchendo um DataSet usando um ou mais REF CURSORs](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|Este exemplo executa um procedimento armazenado PL/SQL, que retorna dois parâmetros de REF CURSOR e preenche um <xref:System.Data.DataSet> com as linhas retornadas.|  
  
 Para usar esses exemplos, você pode precisar criar as tabelas Oracle e deve criar um pacote PL/SQL e o corpo do pacote.  
  
## <a name="creating-the-oracle-tables"></a>Criando as tabelas do Oracle  
 Estes exemplos usam as tabelas que são definidas no esquema Scott/Tiger do Oracle. O esquema Scott/Tiger do Oracle é incluído na maioria das instalações do Oracle. Se esse esquema não existir, você poderá usar o arquivo de comandos SQL em {OracleHome}\rdbms\admin\scott.sql para criar as tabelas e os índices usados por esses exemplos.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Criando o pacote Oracle e o corpo do pacote  
 Esses exemplos requerem o seguinte pacote PL/SQL e o corpo do pacote no seu servidor. Crie o seguinte pacote Oracle no servidor Oracle.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 Crie o seguinte corpo do pacote Oracle no servidor Oracle.  
  
```  
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
  
## <a name="see-also"></a>Consulte também  
 [REF CURSORs do Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
