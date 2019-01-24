---
title: O método Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 06666e069f20bc06f303c4e829d1c69c185a8a84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602475"
---
# <a name="the-load-method"></a><span data-ttu-id="e69ce-102">O método Load</span><span class="sxs-lookup"><span data-stu-id="e69ce-102">The Load Method</span></span>
<span data-ttu-id="e69ce-103">Você pode usar o <xref:System.Data.DataTable.Load%2A> método para carregar um <xref:System.Data.DataTable> com linhas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e69ce-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="e69ce-104">Este é um método sobrecarregado que, em sua forma mais simples, aceita um único parâmetro, uma **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="e69ce-105">Neste formulário, ele simplesmente carrega o **DataTable** com linhas.</span><span class="sxs-lookup"><span data-stu-id="e69ce-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="e69ce-106">Opcionalmente, você pode especificar o **LoadOption** parâmetro para controlar como os dados são adicionados para o **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="e69ce-107">O **LoadOption** parâmetro é particularmente útil em casos em que o **DataTable** já contiver linhas de dados, pois descreve dados de entrada como de fonte de dados serão combinados com os dados já na tabela.</span><span class="sxs-lookup"><span data-stu-id="e69ce-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="e69ce-108">Por exemplo, **PreserveCurrentValues** (o padrão) Especifica que em casos em que uma linha está marcada como **adicionado** no **DataTable**, o **Original** valor ou cada coluna é definida como o conteúdo da linha correspondente da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e69ce-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="e69ce-109">O **atual** valor manterá os valores atribuídos quando a linha foi adicionada e o **RowState** da linha será definido como **Changed**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="e69ce-110">A tabela a seguir fornece uma breve descrição do <xref:System.Data.LoadOption> valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e69ce-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="e69ce-111">Valor de LoadOption</span><span class="sxs-lookup"><span data-stu-id="e69ce-111">LoadOption value</span></span>|<span data-ttu-id="e69ce-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e69ce-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e69ce-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="e69ce-113">**OverwriteRow**</span></span>|<span data-ttu-id="e69ce-114">Se linhas de entrada tiverem o mesmo **PrimaryKey** valor como uma linha já está sendo a **DataTable**, o **Original** e **atual** valores de cada coluna são substituídos pelos valores na nova linha e o **RowState** estiver definida como **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="e69ce-115">Linhas da fonte de dados que ainda não existirem na **DataTable** são adicionados com um **RowState** valor de **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="e69ce-116">Na verdade, essa opção atualiza o conteúdo do **DataTable** para que ele corresponde ao conteúdo da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e69ce-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="e69ce-117">**PreserveCurrentValues (padrão)**</span><span class="sxs-lookup"><span data-stu-id="e69ce-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="e69ce-118">Se linhas de entrada tiverem o mesmo **PrimaryKey** valor como uma linha já está sendo a **DataTable**, o **Original** valor é definido como o conteúdo de linha de entrada e o **Atual** valor não é alterado.</span><span class="sxs-lookup"><span data-stu-id="e69ce-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="e69ce-119">Se o **RowState** é **adicionado** ou **modificado**, ele é definido como **modificado**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="e69ce-120">Se o **RowState** foi **Deleted**, ele permanece **Deleted**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="e69ce-121">Linhas da fonte de dados que ainda não existirem na **DataTable** são adicionados e o **RowState** está definido como **inalterado**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="e69ce-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="e69ce-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="e69ce-123">Se linhas de entrada tiverem o mesmo **PrimaryKey** valor como a linha já está sendo a **DataTable**, o **atual** valor é copiado para o **Original**valor e o **atual** valor é definido como o conteúdo da linha de entrada.</span><span class="sxs-lookup"><span data-stu-id="e69ce-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="e69ce-124">Se o **RowState** na **DataTable** foi **adicionado**, o **RowState** permanece **adicionado**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="e69ce-125">Para linhas marcadas como **Modified** ou **Deleted**, o **RowState** é **modificado**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="e69ce-126">Linhas da fonte de dados que ainda não existirem na **DataTable** são adicionados e o **RowState** está definido como **adicionado**.</span><span class="sxs-lookup"><span data-stu-id="e69ce-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="e69ce-127">O exemplo a seguir usa o **Load** método para exibir uma lista de aniversários para funcionários a **Northwind** banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e69ce-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e69ce-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e69ce-128">See also</span></span>
- [<span data-ttu-id="e69ce-129">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="e69ce-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- <span data-ttu-id="e69ce-130">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e69ce-130">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
