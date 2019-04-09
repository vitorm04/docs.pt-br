---
title: 'Como: Definir o valor exibido pelo controle ProgressBar do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 292a70658e37839897b39d4d58fdf98903d2d963
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196873"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="80c4e-102">Como: Definir o valor exibido pelo controle ProgressBar do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80c4e-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="80c4e-103">O controle <xref:System.Windows.Forms.ToolStripProgressBar> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ProgressBar>, no entanto, o controle <xref:System.Windows.Forms.ProgressBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="80c4e-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="80c4e-104">O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oferece várias maneiras diferentes de exibir um determinado valor dentro de <xref:System.Windows.Forms.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="80c4e-104">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="80c4e-105">A abordagem que você escolher dependerá da tarefa em mãos ou do problema que está resolvendo.</span><span class="sxs-lookup"><span data-stu-id="80c4e-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="80c4e-106">A tabela a seguir mostra as abordagens que você pode escolher.</span><span class="sxs-lookup"><span data-stu-id="80c4e-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="80c4e-107">Abordagem</span><span class="sxs-lookup"><span data-stu-id="80c4e-107">Approach</span></span>|<span data-ttu-id="80c4e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="80c4e-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="80c4e-109">Defina o valor da <xref:System.Windows.Forms.ProgressBar> controlar diretamente.</span><span class="sxs-lookup"><span data-stu-id="80c4e-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="80c4e-110">Essa abordagem é útil para as tarefas em que você sabe que o total do item medido será envolvido, como ler os registros de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="80c4e-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="80c4e-111">Além disso, se você precisar definir o valor uma ou duas vezes, esta será uma maneira fácil de realizar esta tarefa.</span><span class="sxs-lookup"><span data-stu-id="80c4e-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="80c4e-112">Por fim, use esse processo se você precisar diminuir o valor exibido pela barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="80c4e-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="80c4e-113">Aumentar o <xref:System.Windows.Forms.ProgressBar> exibir por um valor fixo.</span><span class="sxs-lookup"><span data-stu-id="80c4e-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="80c4e-114">Essa abordagem será útil quando você estiver exibindo uma contagem simples entre o mínimo e máximo, como o tempo decorrido ou o número de arquivos que foram processados de um total conhecido.</span><span class="sxs-lookup"><span data-stu-id="80c4e-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="80c4e-115">Aumentar o <xref:System.Windows.Forms.ProgressBar> exibir por um valor que varia de acordo.</span><span class="sxs-lookup"><span data-stu-id="80c4e-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="80c4e-116">Essa abordagem será útil quando você precisar alterar o valor exibido várias vezes em volumes diferentes.</span><span class="sxs-lookup"><span data-stu-id="80c4e-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="80c4e-117">Um exemplo seria mostrar a quantidade de espaço em disco consumida durante a gravação de uma série de arquivos no disco.</span><span class="sxs-lookup"><span data-stu-id="80c4e-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="80c4e-118">A maneira mais direta de definir o valor exibido por uma barra de progresso é, definindo o <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="80c4e-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="80c4e-119">Isso pode ser feito no tempo de design ou no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="80c4e-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="80c4e-120">Para definir o valor de ProgressBar diretamente</span><span class="sxs-lookup"><span data-stu-id="80c4e-120">To set the ProgressBar value directly</span></span>  
  
1.  <span data-ttu-id="80c4e-121">Defina as <xref:System.Windows.Forms.ProgressBar> do controle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valores.</span><span class="sxs-lookup"><span data-stu-id="80c4e-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="80c4e-122">No código, defina o controle <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade como um valor inteiro entre os valores mínimos e máximo estabelecidos por você.</span><span class="sxs-lookup"><span data-stu-id="80c4e-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="80c4e-123">Se você definir a <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade fora dos limites estabelecidos pela <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriedades, o controle gera um <xref:System.ArgumentException> exceção.</span><span class="sxs-lookup"><span data-stu-id="80c4e-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="80c4e-124">O exemplo de código a seguir ilustra como definir o <xref:System.Windows.Forms.ProgressBar> valor diretamente.</span><span class="sxs-lookup"><span data-stu-id="80c4e-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="80c4e-125">O código lerá os registros de uma fonte de dados e atualizará a barra de progresso e o rótulo sempre que um registro de dados for lido.</span><span class="sxs-lookup"><span data-stu-id="80c4e-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="80c4e-126">Este exemplo requer que o formulário tem um <xref:System.Windows.Forms.Label> controle, um <xref:System.Windows.Forms.ProgressBar> controle e uma tabela de dados com uma linha chamada `CustomerRow` com `FirstName` e `LastName` campos.</span><span class="sxs-lookup"><span data-stu-id="80c4e-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     Se você estiver exibindo o progresso que passa por um intervalo fixo, você pode definir o valor e, em seguida, chamar um método que aumenta a <xref:System.Windows.Forms.ProgressBar> o valor do controle por intervalo. <span data-ttu-id="80c4e-128">Isso é útil para temporizadores e outros cenários em que você não esteja medindo o andamento como um percentual do todo.</span><span class="sxs-lookup"><span data-stu-id="80c4e-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="80c4e-129">Para aumentar a barra de progresso com um valor fixo</span><span class="sxs-lookup"><span data-stu-id="80c4e-129">To increase the progress bar by a fixed value</span></span>  
  
1.  <span data-ttu-id="80c4e-130">Defina as <xref:System.Windows.Forms.ProgressBar> do controle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valores.</span><span class="sxs-lookup"><span data-stu-id="80c4e-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="80c4e-131">Defina o controle <xref:System.Windows.Forms.ProgressBar.Step%2A> valor exibido de propriedade em um inteiro que representa a quantidade para aumentar a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="80c4e-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3.  <span data-ttu-id="80c4e-132">Chame o <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> método para alterar o valor exibido pela quantidade definida <xref:System.Windows.Forms.ProgressBar.Step%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="80c4e-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="80c4e-133">O exemplo de código a seguir ilustra como uma barra de progresso pode manter uma contagem de arquivos em uma operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="80c4e-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="80c4e-134">No exemplo a seguir, como cada arquivo é lido na memória, a barra de progresso e o rótulo são atualizados para refletir a quantidade total de arquivos lidos.</span><span class="sxs-lookup"><span data-stu-id="80c4e-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="80c4e-135">Este exemplo requer que o formulário tem um <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="80c4e-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     Por fim, você pode aumentar o valor exibido por uma barra de progresso para que cada aumento seja um valor exclusivo. <span data-ttu-id="80c4e-137">Isso será útil quando você estiver controlando uma série de operações exclusivas, como gravar arquivos de tamanhos diferentes em um disco rígido ou medir o progresso como um percentual do todo.</span><span class="sxs-lookup"><span data-stu-id="80c4e-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="80c4e-138">Para aumentar a barra de progresso com um valor dinâmico</span><span class="sxs-lookup"><span data-stu-id="80c4e-138">To increase the progress bar by a dynamic value</span></span>  
  
1.  <span data-ttu-id="80c4e-139">Defina as <xref:System.Windows.Forms.ProgressBar> do controle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valores.</span><span class="sxs-lookup"><span data-stu-id="80c4e-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="80c4e-140">Chamar o <xref:System.Windows.Forms.ProgressBar.Increment%2A> método para alterar o valor exibido por um número inteiro que você especificar.</span><span class="sxs-lookup"><span data-stu-id="80c4e-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="80c4e-141">O exemplo de código a seguir ilustra como uma barra de progresso pode calcular a quantidade de espaço em disco usado durante uma operação de cópia.</span><span class="sxs-lookup"><span data-stu-id="80c4e-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="80c4e-142">No exemplo a seguir, como cada arquivo é gravado no disco rígido, a barra de progresso e o rótulo são atualizados para refletir a quantidade de espaço em disco disponível.</span><span class="sxs-lookup"><span data-stu-id="80c4e-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="80c4e-143">Este exemplo requer que o formulário tem um <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="80c4e-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="80c4e-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80c4e-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="80c4e-145">Visão geral do controle ProgressBar</span><span class="sxs-lookup"><span data-stu-id="80c4e-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="80c4e-146">Controle ProgressBar</span><span class="sxs-lookup"><span data-stu-id="80c4e-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
