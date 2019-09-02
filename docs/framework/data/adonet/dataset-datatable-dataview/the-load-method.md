---
title: O método Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: b704deeffcd06bca09b6c26d60a66218b46fc55c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203173"
---
# <a name="the-load-method"></a><span data-ttu-id="22c78-102">O método Load</span><span class="sxs-lookup"><span data-stu-id="22c78-102">The Load Method</span></span>
<span data-ttu-id="22c78-103">Você pode usar o <xref:System.Data.DataTable.Load%2A> método para carregar um <xref:System.Data.DataTable> com linhas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="22c78-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="22c78-104">Esse é um método sobrecarregado que, em sua forma mais simples, aceita um único parâmetro, um **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="22c78-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="22c78-105">Neste formulário, ele simplesmente carrega a **DataTable** com linhas.</span><span class="sxs-lookup"><span data-stu-id="22c78-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="22c78-106">Opcionalmente, você pode especificar o parâmetro **LoadOption** para controlar como os dados são adicionados à **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="22c78-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="22c78-107">O parâmetro **LoadOption** é particularmente útil nos casos em que **DataTable** já contém linhas de dados, pois descreve como os dados de entrada da fonte de dados serão combinados com os dados que já estão na tabela.</span><span class="sxs-lookup"><span data-stu-id="22c78-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="22c78-108">Por exemplo, **PreserveCurrentValues** (o padrão) especifica que, nos casos em que uma linha é marcada como **adicionada** à **DataTable**, o valor **original** ou cada coluna é definido como o conteúdo da linha correspondente da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="22c78-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="22c78-109">O valor **atual** manterá os valores atribuídos quando a linha foi adicionada e o **RowState** da linha será definido como **alterado**.</span><span class="sxs-lookup"><span data-stu-id="22c78-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="22c78-110">A tabela a seguir fornece uma breve descrição dos <xref:System.Data.LoadOption> valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="22c78-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="22c78-111">Valor de LoadOption</span><span class="sxs-lookup"><span data-stu-id="22c78-111">LoadOption value</span></span>|<span data-ttu-id="22c78-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="22c78-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="22c78-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="22c78-113">**OverwriteRow**</span></span>|<span data-ttu-id="22c78-114">Se as linhas de entrada tiverem o mesmo valor de **PrimaryKey** que uma linha já na **DataTable**, os valores **original** e **atual** de cada coluna serão substituídos pelos valores na linha de entrada e a propriedade **RowState** será definida como **Inalterado**.</span><span class="sxs-lookup"><span data-stu-id="22c78-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="22c78-115">As linhas da fonte de dados que ainda não existem na **DataTable** são adicionadas com um valor de RowStatede inalterado.</span><span class="sxs-lookup"><span data-stu-id="22c78-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="22c78-116">Essa opção em vigor atualiza o conteúdo da **DataTable** para que ela corresponda ao conteúdo da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="22c78-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="22c78-117">**PreserveCurrentValues (padrão)**</span><span class="sxs-lookup"><span data-stu-id="22c78-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="22c78-118">Se as linhas de entrada tiverem o mesmo valor de **PrimaryKey** que uma linha já na **DataTable**, o valor **original** será definido como o conteúdo da linha de entrada e o valor **atual** não será alterado.</span><span class="sxs-lookup"><span data-stu-id="22c78-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="22c78-119">Se o **RowState** for **adicionado** ou **modificado**, ele será definido como **modificado**.</span><span class="sxs-lookup"><span data-stu-id="22c78-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="22c78-120">Se o **RowState** tiver sido **excluído**, ele permanecerá **excluído**.</span><span class="sxs-lookup"><span data-stu-id="22c78-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="22c78-121">As linhas da fonte de dados que ainda não existem na **DataTable** são adicionadas e o **RowState** é definido como inalterado.</span><span class="sxs-lookup"><span data-stu-id="22c78-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="22c78-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="22c78-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="22c78-123">Se as linhas de entrada tiverem o mesmo valor de **PrimaryKey** que a linha já na **DataTable**, o valor **atual** será copiado para o valor **original** e o valor **atual** será definido como o conteúdo da linha de entrada.</span><span class="sxs-lookup"><span data-stu-id="22c78-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="22c78-124">Se o **RowState** na **DataTable** tiver sido **adicionado**, o **RowState** permanecerá **adicionado**.</span><span class="sxs-lookup"><span data-stu-id="22c78-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="22c78-125">Para linhas marcadas como modificadas ou **excluídas**, o **RowState** é **modificado**.</span><span class="sxs-lookup"><span data-stu-id="22c78-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="22c78-126">As linhas da fonte de dados que ainda não existem na **DataTable** são adicionadas e o **RowState** é definido como **adicionado**.</span><span class="sxs-lookup"><span data-stu-id="22c78-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="22c78-127">O exemplo a seguir usa o método **Load** para exibir uma lista de aniversários para os funcionários no banco de dados **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="22c78-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22c78-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22c78-128">See also</span></span>

- [<span data-ttu-id="22c78-129">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="22c78-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- <span data-ttu-id="22c78-130">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="22c78-130">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
