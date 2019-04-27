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
ms.openlocfilehash: 42a9e0f67f00c1a706b72ab0eeb522e99d8a8dfe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912841"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Como: Definir o valor exibido pelo controle ProgressBar do Windows Forms
> [!IMPORTANT]
>  O controle <xref:System.Windows.Forms.ToolStripProgressBar> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ProgressBar>, no entanto, o controle <xref:System.Windows.Forms.ProgressBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oferece várias maneiras diferentes de exibir um determinado valor dentro de <xref:System.Windows.Forms.ProgressBar> controle. A abordagem que você escolher dependerá da tarefa em mãos ou do problema que está resolvendo. A tabela a seguir mostra as abordagens que você pode escolher.  
  
|Abordagem|Descrição|  
|--------------|-----------------|  
|Defina o valor da <xref:System.Windows.Forms.ProgressBar> controlar diretamente.|Essa abordagem é útil para as tarefas em que você sabe que o total do item medido será envolvido, como ler os registros de uma fonte de dados. Além disso, se você precisar definir o valor uma ou duas vezes, esta será uma maneira fácil de realizar esta tarefa. Por fim, use esse processo se você precisar diminuir o valor exibido pela barra de progresso.|  
|Aumentar o <xref:System.Windows.Forms.ProgressBar> exibir por um valor fixo.|Essa abordagem será útil quando você estiver exibindo uma contagem simples entre o mínimo e máximo, como o tempo decorrido ou o número de arquivos que foram processados de um total conhecido.|  
|Aumentar o <xref:System.Windows.Forms.ProgressBar> exibir por um valor que varia de acordo.|Essa abordagem será útil quando você precisar alterar o valor exibido várias vezes em volumes diferentes. Um exemplo seria mostrar a quantidade de espaço em disco consumida durante a gravação de uma série de arquivos no disco.|  
  
 A maneira mais direta de definir o valor exibido por uma barra de progresso é, definindo o <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade. Isso pode ser feito no tempo de design ou no tempo de execução.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Para definir o valor de ProgressBar diretamente  
  
1. Defina as <xref:System.Windows.Forms.ProgressBar> do controle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valores.  
  
2. No código, defina o controle <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade como um valor inteiro entre os valores mínimos e máximo estabelecidos por você.  
  
    > [!NOTE]
    >  Se você definir a <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade fora dos limites estabelecidos pela <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriedades, o controle gera um <xref:System.ArgumentException> exceção.  
  
     O exemplo de código a seguir ilustra como definir o <xref:System.Windows.Forms.ProgressBar> valor diretamente. O código lerá os registros de uma fonte de dados e atualizará a barra de progresso e o rótulo sempre que um registro de dados for lido. Este exemplo requer que o formulário tem um <xref:System.Windows.Forms.Label> controle, um <xref:System.Windows.Forms.ProgressBar> controle e uma tabela de dados com uma linha chamada `CustomerRow` com `FirstName` e `LastName` campos.  
  
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
  
     Se você estiver exibindo o progresso que passa por um intervalo fixo, você pode definir o valor e, em seguida, chamar um método que aumenta a <xref:System.Windows.Forms.ProgressBar> o valor do controle por intervalo. Isso é útil para temporizadores e outros cenários em que você não esteja medindo o andamento como um percentual do todo.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Para aumentar a barra de progresso com um valor fixo  
  
1. Defina as <xref:System.Windows.Forms.ProgressBar> do controle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valores.  
  
2. Defina o controle <xref:System.Windows.Forms.ProgressBar.Step%2A> valor exibido de propriedade em um inteiro que representa a quantidade para aumentar a barra de progresso.  
  
3. Chame o <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> método para alterar o valor exibido pela quantidade definida <xref:System.Windows.Forms.ProgressBar.Step%2A> propriedade.  
  
     O exemplo de código a seguir ilustra como uma barra de progresso pode manter uma contagem de arquivos em uma operação de cópia.  
  
     No exemplo a seguir, como cada arquivo é lido na memória, a barra de progresso e o rótulo são atualizados para refletir a quantidade total de arquivos lidos. Este exemplo requer que o formulário tem um <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.ProgressBar> controle.  
  
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
  
     Por fim, você pode aumentar o valor exibido por uma barra de progresso para que cada aumento seja um valor exclusivo. Isso será útil quando você estiver controlando uma série de operações exclusivas, como gravar arquivos de tamanhos diferentes em um disco rígido ou medir o progresso como um percentual do todo.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Para aumentar a barra de progresso com um valor dinâmico  
  
1. Defina as <xref:System.Windows.Forms.ProgressBar> do controle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valores.  
  
2. Chamar o <xref:System.Windows.Forms.ProgressBar.Increment%2A> método para alterar o valor exibido por um número inteiro que você especificar.  
  
     O exemplo de código a seguir ilustra como uma barra de progresso pode calcular a quantidade de espaço em disco usado durante uma operação de cópia.  
  
     No exemplo a seguir, como cada arquivo é gravado no disco rígido, a barra de progresso e o rótulo são atualizados para refletir a quantidade de espaço em disco disponível. Este exemplo requer que o formulário tem um <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.ProgressBar> controle.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [Visão geral do controle ProgressBar](progressbar-control-overview-windows-forms.md)
- [Controle ProgressBar](progressbar-control-windows-forms.md)
