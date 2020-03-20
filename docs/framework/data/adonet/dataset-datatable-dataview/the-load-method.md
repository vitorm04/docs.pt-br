---
title: O método Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150721"
---
# <a name="the-load-method"></a><span data-ttu-id="196e0-102">O método Load</span><span class="sxs-lookup"><span data-stu-id="196e0-102">The Load Method</span></span>
<span data-ttu-id="196e0-103">Você pode <xref:System.Data.DataTable.Load%2A> usar o <xref:System.Data.DataTable> método para carregar um com linhas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="196e0-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="196e0-104">Trata-se de um método sobrecarregado que, em sua forma mais simples, aceita um único parâmetro, um **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="196e0-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="196e0-105">Neste formulário, ele simplesmente carrega a **Tabela de Dados** com linhas.</span><span class="sxs-lookup"><span data-stu-id="196e0-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="196e0-106">Opcionalmente, você pode especificar o parâmetro **LoadOption** para controlar como os dados são adicionados à **Tabela de Dados**.</span><span class="sxs-lookup"><span data-stu-id="196e0-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="196e0-107">O parâmetro **LoadOption** é particularmente útil nos casos em que a Tabela de **Dados** já contém linhas de dados, porque descreve como os dados recebidas da fonte de dados serão combinados com os dados já na tabela.</span><span class="sxs-lookup"><span data-stu-id="196e0-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="196e0-108">Por exemplo, **PreserveCurrentValues** (o padrão) especifica que nos casos em que uma linha é marcada como **Adicionada** na **Tabela de Dados,** o valor **Original** ou cada coluna é definido para o conteúdo da linha correspondente da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="196e0-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="196e0-109">O valor **Atual** manterá os valores atribuídos quando a linha foi adicionada e o Estado de **linha** da linha será definido como **Alterado**.</span><span class="sxs-lookup"><span data-stu-id="196e0-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="196e0-110">A tabela a seguir fornece <xref:System.Data.LoadOption> uma breve descrição dos valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="196e0-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="196e0-111">Valor loadOption</span><span class="sxs-lookup"><span data-stu-id="196e0-111">LoadOption value</span></span>|<span data-ttu-id="196e0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="196e0-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="196e0-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="196e0-113">**OverwriteRow**</span></span>|<span data-ttu-id="196e0-114">Se as linhas recebidas tiverem o mesmo valor **PrimaryKey** de uma linha já existente na Tabela de **Dados,** os valores **Original** e **Atual** de cada coluna serão substituídos pelos valores na linha de entrada e a propriedade **RowState** será definida **como Inalterada**.</span><span class="sxs-lookup"><span data-stu-id="196e0-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="196e0-115">As linhas da fonte de dados que ainda não existem na **Tabela de Dados** são adicionadas com um valor **rowState** de **Inalterado**.</span><span class="sxs-lookup"><span data-stu-id="196e0-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="196e0-116">Esta opção, na verdade, atualiza o conteúdo da Tabela de **Dados** para que corresponda ao conteúdo da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="196e0-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="196e0-117">**PreservarValors de corrente (padrão)**</span><span class="sxs-lookup"><span data-stu-id="196e0-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="196e0-118">Se as linhas recebidas tiverem o mesmo valor **PrimaryKey** de uma linha já na **Tabela de Dados,** o valor **Original** será definido para o conteúdo da linha de entrada e o valor **Atual** não será alterado.</span><span class="sxs-lookup"><span data-stu-id="196e0-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="196e0-119">Se o **Estado de linha for** **adicionado** ou **modificado,** ele será definido como **Modificado**.</span><span class="sxs-lookup"><span data-stu-id="196e0-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="196e0-120">Se o **RowState foi** **excluído,** ele será **excluído**.</span><span class="sxs-lookup"><span data-stu-id="196e0-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="196e0-121">As linhas da fonte de dados que ainda não existem na **Tabela de Dados** são adicionadas e o **RowState** é definido **como Inalterado**.</span><span class="sxs-lookup"><span data-stu-id="196e0-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="196e0-122">**AtualizaçãoAtualValores**</span><span class="sxs-lookup"><span data-stu-id="196e0-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="196e0-123">Se as linhas recebidas tiverem o mesmo valor **PrimaryKey** da linha já na **Tabela de Dados,** o valor **Atual** será copiado para o valor **Original** e o valor **Atual** será definido para o conteúdo da linha de entrada.</span><span class="sxs-lookup"><span data-stu-id="196e0-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="196e0-124">Se o **Estado de Linha** na Tabela de **Dados** foi **adicionado,** o **Estado de linha** permanece **adicionado**.</span><span class="sxs-lookup"><span data-stu-id="196e0-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="196e0-125">Para linhas marcadas como **Modificadas** ou **Excluídas,** o **Estado de linha** é **modificado**.</span><span class="sxs-lookup"><span data-stu-id="196e0-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="196e0-126">As linhas da fonte de dados que ainda não existem na **Tabela de dados** são adicionadas e o **RowState** é definido **como Adicionado**.</span><span class="sxs-lookup"><span data-stu-id="196e0-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="196e0-127">A amostra a seguir usa o método **Load** para exibir uma lista de aniversários para os funcionários no banco de dados **Northwind.**</span><span class="sxs-lookup"><span data-stu-id="196e0-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="196e0-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="196e0-128">See also</span></span>

- [<span data-ttu-id="196e0-129">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="196e0-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="196e0-130">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="196e0-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
