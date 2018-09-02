---
title: Recuperando dados binários
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: ec4ef17687e4e1bf2cc18182a64fc7361fe3b6f7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421977"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="34de3-102">Recuperando dados binários</span><span class="sxs-lookup"><span data-stu-id="34de3-102">Retrieving Binary Data</span></span>
<span data-ttu-id="34de3-103">Por padrão, o **DataReader** carrega dados de entrada como uma linha assim que uma linha inteira de dados está disponível.</span><span class="sxs-lookup"><span data-stu-id="34de3-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="34de3-104">Os blobs precisam de tratamento diferente, no entanto, porque podem conter gigabytes de dados que não podem ser contidos em uma única linha.</span><span class="sxs-lookup"><span data-stu-id="34de3-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="34de3-105">O **ExecuteReader** método tem uma sobrecarga que levará um <xref:System.Data.CommandBehavior> argumento para modificar o comportamento padrão do **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="34de3-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="34de3-106">Você pode passar <xref:System.Data.CommandBehavior.SequentialAccess> para o **ExecuteReader** método para modificar o comportamento padrão do **DataReader** para que, em vez de carregar linhas de dados, ele carregará dados sequencialmente conforme ela é recebida.</span><span class="sxs-lookup"><span data-stu-id="34de3-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="34de3-107">Isso é ideal para carregar BLOBs ou outras estruturas grandes de dados.</span><span class="sxs-lookup"><span data-stu-id="34de3-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="34de3-108">Observe que esse comportamento pode depender da sua fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="34de3-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="34de3-109">Por exemplo, retornar um BLOB do Microsoft Access carregará o BLOB inteiro que está sendo carregado na memória, em vez de em sequência à medida que é recebido.</span><span class="sxs-lookup"><span data-stu-id="34de3-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="34de3-110">Ao definir a **DataReader** usar **SequentialAccess**, é importante observar a sequência na qual você acessa os campos retornados.</span><span class="sxs-lookup"><span data-stu-id="34de3-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="34de3-111">O comportamento padrão do **DataReader**, que carrega uma linha inteira assim que estiver disponível, permite que você acesse os campos retornados em qualquer ordem, até que a próxima linha seja lida.</span><span class="sxs-lookup"><span data-stu-id="34de3-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="34de3-112">Ao usar **SequentialAccess** no entanto, você deve acessar os campos retornados pela **DataReader** na ordem.</span><span class="sxs-lookup"><span data-stu-id="34de3-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="34de3-113">Por exemplo, se sua consulta retornar três colunas, a terceiro das quais é um BLOB, você deverá retornar os valores do primeiro campo e do segundo antes de acessar os dados de BLOB no terceiro campo.</span><span class="sxs-lookup"><span data-stu-id="34de3-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="34de3-114">Se você acessar o terceiro campo antes do primeiro campo ou segundo, o primeiro e o segundo valores de campo não estarão mais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="34de3-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="34de3-115">Isso ocorre porque **SequentialAccess** tiver modificado o **DataReader** retornar dados em sequência e os dados não estará disponível após o **DataReader** tiver lido depois deles.</span><span class="sxs-lookup"><span data-stu-id="34de3-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="34de3-116">Ao acessar os dados no campo de BLOB, use o **GetBytes** ou **GetChars** digitou acessadores dos **DataReader**, que preenchem uma matriz com os dados.</span><span class="sxs-lookup"><span data-stu-id="34de3-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="34de3-117">Você também pode usar **GetString** para dados de caracteres; no entanto.</span><span class="sxs-lookup"><span data-stu-id="34de3-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="34de3-118">para conservar os recursos do sistema, você pode não querer carregar um valor inteiro de BLOB em uma única variável de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="34de3-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="34de3-119">Em vez disso, você pode especificar um tamanho do buffer específico de dados a serem retornados e um local inicial para que o primeiro byte ou caractere seja lido dos dados retornados.</span><span class="sxs-lookup"><span data-stu-id="34de3-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="34de3-120">**GetBytes** e **GetChars** retornará um `long` valor, que representa o número de bytes ou caracteres retornados.</span><span class="sxs-lookup"><span data-stu-id="34de3-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="34de3-121">Se você passar um array nulo para **GetBytes** ou **GetChars**, o valor longo retornado será o número total de bytes ou caracteres no BLOB.</span><span class="sxs-lookup"><span data-stu-id="34de3-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="34de3-122">Você pode opcionalmente especificar um índice na matriz como uma posição inicial para os dados que estão sendo lidos.</span><span class="sxs-lookup"><span data-stu-id="34de3-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34de3-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34de3-123">Example</span></span>  
 <span data-ttu-id="34de3-124">O exemplo a seguir retorna a ID do publicador e o logotipo do **pubs** banco de dados de exemplo no Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="34de3-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="34de3-125">A ID do publicador (`pub_id`) é um campo de caracteres e o logotipo é uma imagem, que é um BLOB.</span><span class="sxs-lookup"><span data-stu-id="34de3-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="34de3-126">Porque o **logotipo** campo é um bitmap, o exemplo retorna dados binários usando **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="34de3-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="34de3-127">Observe que a ID do publicador é acessada para a linha atual de dados antes do logotipo, porque os campos devem ser acessados sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="34de3-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="34de3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34de3-128">See Also</span></span>  
 [<span data-ttu-id="34de3-129">Trabalhando com DataReaders</span><span class="sxs-lookup"><span data-stu-id="34de3-129">Working with DataReaders</span></span>](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 <span data-ttu-id="34de3-130">[SQL Server Binary and Large-Value Data](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="34de3-130">[SQL Server Binary and Large-Value Data](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)</span></span>  
 <span data-ttu-id="34de3-131">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="34de3-131">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
