---
title: O método Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 04defffc724875e691fd7b87331c28e6b6c0cd28
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="the-load-method"></a><span data-ttu-id="e2899-102">O método Load</span><span class="sxs-lookup"><span data-stu-id="e2899-102">The Load Method</span></span>
<span data-ttu-id="e2899-103">Você pode usar o <xref:System.Data.DataTable.Load%2A> método para carregar um <xref:System.Data.DataTable> com linhas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e2899-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="e2899-104">Este é um método sobrecarregado que, em sua forma mais simples, aceita um único parâmetro, um **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="e2899-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="e2899-105">Neste formulário, ele simplesmente carrega o **DataTable** com linhas.</span><span class="sxs-lookup"><span data-stu-id="e2899-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="e2899-106">Opcionalmente, você pode especificar o **LoadOption** parâmetro para controlar como os dados são adicionados para o **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="e2899-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="e2899-107">O **LoadOption** parâmetro é particularmente útil em casos onde o **DataTable** já contém linhas de dados, porque ele descreve como entrados dados da fonte de dados serão combinados com os dados já está na tabela.</span><span class="sxs-lookup"><span data-stu-id="e2899-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="e2899-108">Por exemplo, **PreserveCurrentValues** (o padrão) Especifica que em casos em que uma linha é marcada como **adicionado** no **DataTable**, o **Original** valor ou cada coluna é definida para o conteúdo da linha correspondente da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e2899-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="e2899-109">O **atual** valor manterá os valores atribuídos quando a linha foi adicionada e o **RowState** da linha será definido como **alterado**.</span><span class="sxs-lookup"><span data-stu-id="e2899-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="e2899-110">A tabela a seguir fornece uma breve descrição do <xref:System.Data.LoadOption> valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e2899-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="e2899-111">Valor de LoadOption</span><span class="sxs-lookup"><span data-stu-id="e2899-111">LoadOption value</span></span>|<span data-ttu-id="e2899-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2899-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e2899-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="e2899-113">**OverwriteRow**</span></span>|<span data-ttu-id="e2899-114">Se as linhas de entrada têm o mesmo **PrimaryKey** valor como uma linha já está sendo o **DataTable**, o **Original** e **atual** valores de cada coluna são substituídos pelos valores na linha de entrada e o **RowState** está definida como **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="e2899-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="e2899-115">Linhas da fonte de dados que ainda não existir o **DataTable** são adicionados a um **RowState** valor de **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="e2899-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="e2899-116">Essa opção em vigor atualiza o conteúdo do **DataTable** para que ele corresponda o conteúdo da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e2899-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="e2899-117">**PreserveCurrentValues (padrão)**</span><span class="sxs-lookup"><span data-stu-id="e2899-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="e2899-118">Se as linhas de entrada têm o mesmo **PrimaryKey** valor como uma linha já está sendo o **DataTable**, o **Original** valor é definido como o conteúdo da linha de entrada e o **Atual** valor não é alterado.</span><span class="sxs-lookup"><span data-stu-id="e2899-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="e2899-119">Se o **RowState** é **adicionado** ou **modificadas**, ele é definido como **modificadas**.</span><span class="sxs-lookup"><span data-stu-id="e2899-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="e2899-120">Se o **RowState** foi **excluído**, ele permanece **excluído**.</span><span class="sxs-lookup"><span data-stu-id="e2899-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="e2899-121">Linhas da fonte de dados que ainda não existir o **DataTable** são adicionados e o **RowState** é definido como **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="e2899-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="e2899-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="e2899-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="e2899-123">Se as linhas de entrada têm o mesmo **PrimaryKey** valor como a linha já está sendo o **DataTable**, o **atual** valor é copiado para o **Original**valor e o **atual** valor é definido como o conteúdo da linha de entrada.</span><span class="sxs-lookup"><span data-stu-id="e2899-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="e2899-124">Se o **RowState** no **DataTable** foi **adicionado**, o **RowState** permanece **adicionado**.</span><span class="sxs-lookup"><span data-stu-id="e2899-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="e2899-125">Para as linhas marcadas como **modificadas** ou **excluído**, o **RowState** é **modificadas**.</span><span class="sxs-lookup"><span data-stu-id="e2899-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="e2899-126">Linhas da fonte de dados que ainda não existir o **DataTable** são adicionados e o **RowState** é definido como **adicionado**.</span><span class="sxs-lookup"><span data-stu-id="e2899-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="e2899-127">O exemplo a seguir usa o **carga** método para exibir uma lista de aniversários para funcionários a **Northwind** banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e2899-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2899-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2899-128">See Also</span></span>  
 [<span data-ttu-id="e2899-129">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="e2899-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="e2899-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e2899-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
