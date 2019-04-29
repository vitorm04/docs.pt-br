---
title: 'Como: Usar um thread em segundo plano para pesquisar arquivos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Multithreaded Windows Forms Control sample [Windows Forms]
- custom controls [Windows Forms], multithreading
- threading [Windows Forms], custom controls
- custom controls [Windows Forms], samples
ms.assetid: 7fe3956f-5b8f-4f78-8aae-c9eb0b28f13a
ms.openlocfilehash: 806cb2b69d83fae2f73583111d0094c7e86e3c61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785847"
---
# <a name="how-to-use-a-background-thread-to-search-for-files"></a><span data-ttu-id="0c881-102">Como: Usar um thread em segundo plano para pesquisar arquivos</span><span class="sxs-lookup"><span data-stu-id="0c881-102">How to: Use a Background Thread to Search for Files</span></span>
<span data-ttu-id="0c881-103">O <xref:System.ComponentModel.BackgroundWorker> componente substitui e adiciona funcionalidade para o <xref:System.Threading> namespace; no entanto, o <xref:System.Threading> é mantido para compatibilidade com versões anteriores e uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="0c881-103">The <xref:System.ComponentModel.BackgroundWorker> component replaces and adds functionality to the <xref:System.Threading> namespace; however, the <xref:System.Threading> namespace is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="0c881-104">Para obter mais informações, consulte [Visão Geral do Componente BackgroundWorker](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0c881-104">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
 <span data-ttu-id="0c881-105">O Windows Forms usa o modelo de single-threaded apartment (STA), pois Windows Forms é baseado em janelas nativas do Win32, que são inerentemente STA.</span><span class="sxs-lookup"><span data-stu-id="0c881-105">Windows Forms uses the single-threaded apartment (STA) model because Windows Forms is based on native Win32 windows that are inherently apartment-threaded.</span></span> <span data-ttu-id="0c881-106">O modelo STA implica que uma janela pode ser criada em qualquer thread, mas ela não pode mudar os threads já criados e todas as chamadas de função a ela devem ocorrer em seu thread de criação.</span><span class="sxs-lookup"><span data-stu-id="0c881-106">The STA model implies that a window can be created on any thread, but it cannot switch threads once created, and all function calls to it must occur on its creation thread.</span></span> <span data-ttu-id="0c881-107">Fora do Windows Forms, as classes do .NET Framework usam o modelo de threading livre.</span><span class="sxs-lookup"><span data-stu-id="0c881-107">Outside Windows Forms, classes in the .NET Framework use the free threading model.</span></span> <span data-ttu-id="0c881-108">Para obter informações sobre threading no .NET Framework, consulte [Threading](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="0c881-108">For information about threading in the .NET Framework, see [Threading](../../../standard/threading/index.md).</span></span>  
  
 <span data-ttu-id="0c881-109">O modelo STA exige que qualquer método em um controle que precise ser chamado de fora do thread de criação do controle deve realizar marshaling (ser executado no) thread de criação do controle.</span><span class="sxs-lookup"><span data-stu-id="0c881-109">The STA model requires that any methods on a control that need to be called from outside the control's creation thread must be marshaled to (executed on) the control's creation thread.</span></span> <span data-ttu-id="0c881-110">A classe base <xref:System.Windows.Forms.Control> fornece vários métodos (<xref:System.Windows.Forms.Control.Invoke%2A>, <xref:System.Windows.Forms.Control.BeginInvoke%2A>, e <xref:System.Windows.Forms.Control.EndInvoke%2A>) para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="0c881-110">The base class <xref:System.Windows.Forms.Control> provides several methods (<xref:System.Windows.Forms.Control.Invoke%2A>, <xref:System.Windows.Forms.Control.BeginInvoke%2A>, and <xref:System.Windows.Forms.Control.EndInvoke%2A>) for this purpose.</span></span> <span data-ttu-id="0c881-111"><xref:System.Windows.Forms.Control.Invoke%2A> faz chamadas de método síncrono; <xref:System.Windows.Forms.Control.BeginInvoke%2A> faz chamadas de método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="0c881-111"><xref:System.Windows.Forms.Control.Invoke%2A> makes synchronous method calls; <xref:System.Windows.Forms.Control.BeginInvoke%2A> makes asynchronous method calls.</span></span>  
  
 <span data-ttu-id="0c881-112">Se o multithreading for usado no controle em tarefas com uso intensivo de recursos, a interface do usuário poderá permanecer responsiva enquanto uma computação com uso intensivo de recursos é executada em um thread de tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="0c881-112">If you use multithreading in your control for resource-intensive tasks, the user interface can remain responsive while a resource-intensive computation executes on a background thread.</span></span>  
  
 <span data-ttu-id="0c881-113">O exemplo a seguir (`DirectorySearcher`) mostra um controle do Windows Forms com multithread que usa um thread em segundo plano para pesquisar recursivamente arquivos de um diretório que correspondam a uma cadeia de caracteres de pesquisa especificada e, em seguida, preenche uma caixa de listagem com o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0c881-113">The following sample (`DirectorySearcher`) shows a multithreaded Windows Forms control that uses a background thread to recursively search a directory for files matching a specified search string and then populates a list box with the search result.</span></span> <span data-ttu-id="0c881-114">Os principais conceitos ilustrados pelo exemplo são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0c881-114">The key concepts illustrated by the sample are as follows:</span></span>  
  
- <span data-ttu-id="0c881-115">`DirectorySearcher` inicia um novo thread para executar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0c881-115">`DirectorySearcher` starts a new thread to perform the search.</span></span> <span data-ttu-id="0c881-116">O thread executa o método `ThreadProcedure` que, por sua vez, chama o método `RecurseDirectory` auxiliar para fazer a pesquisa e preencher a caixa de listagem.</span><span class="sxs-lookup"><span data-stu-id="0c881-116">The thread executes the `ThreadProcedure` method that in turn calls the helper `RecurseDirectory` method to do the actual search and to populate the list box.</span></span> <span data-ttu-id="0c881-117">No entanto, preencher a caixa de listagem exige uma chamada entre threads, conforme explicado nos próximos dois itens com marcadores.</span><span class="sxs-lookup"><span data-stu-id="0c881-117">However, populating the list box requires a cross-thread call, as explained in the next two bulleted items.</span></span>  
  
- <span data-ttu-id="0c881-118">`DirectorySearcher` define o método `AddFiles` para adicionar arquivos a uma caixa de listagem; no entanto, `RecurseDirectory` não pode invocar diretamente `AddFiles`, porque `AddFiles` pode executar somente no thread de STA que criou `DirectorySearcher`.</span><span class="sxs-lookup"><span data-stu-id="0c881-118">`DirectorySearcher` defines the `AddFiles` method to add files to a list box; however, `RecurseDirectory` cannot directly invoke `AddFiles` because `AddFiles` can execute only in the STA thread that created `DirectorySearcher`.</span></span>  
  
- <span data-ttu-id="0c881-119">A única maneira `RecurseDirectory` pode chamar `AddFiles` é por meio de uma chamada entre threads — ou seja, chamando <xref:System.Windows.Forms.Control.Invoke%2A> ou <xref:System.Windows.Forms.Control.BeginInvoke%2A> para realizar marshaling `AddFiles` para o thread de criação de `DirectorySearcher`.</span><span class="sxs-lookup"><span data-stu-id="0c881-119">The only way `RecurseDirectory` can call `AddFiles` is through a cross-thread call — that is, by calling <xref:System.Windows.Forms.Control.Invoke%2A> or <xref:System.Windows.Forms.Control.BeginInvoke%2A> to marshal `AddFiles` to the creation thread of `DirectorySearcher`.</span></span> <span data-ttu-id="0c881-120">`RecurseDirectory` usa <xref:System.Windows.Forms.Control.BeginInvoke%2A> para que a chamada pode ser feita de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="0c881-120">`RecurseDirectory` uses <xref:System.Windows.Forms.Control.BeginInvoke%2A> so that the call can be made asynchronously.</span></span>  
  
- <span data-ttu-id="0c881-121">O marshaling de um método requer o equivalente de um ponteiro de função ou retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0c881-121">Marshaling a method requires the equivalent of a function pointer or callback.</span></span> <span data-ttu-id="0c881-122">Isso é feito usando delegados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c881-122">This is accomplished using delegates in the .NET Framework.</span></span> <span data-ttu-id="0c881-123"><xref:System.Windows.Forms.Control.BeginInvoke%2A> aceita um delegado como um argumento.</span><span class="sxs-lookup"><span data-stu-id="0c881-123"><xref:System.Windows.Forms.Control.BeginInvoke%2A> takes a delegate as an argument.</span></span> <span data-ttu-id="0c881-124">`DirectorySearcher` Portanto, define um delegado (`FileListDelegate`), associa `AddFiles` a uma instância do `FileListDelegate` em seu construtor e passa essa instância delegada para <xref:System.Windows.Forms.Control.BeginInvoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c881-124">`DirectorySearcher` therefore defines a delegate (`FileListDelegate`), binds `AddFiles` to an instance of `FileListDelegate` in its constructor, and passes this delegate instance to <xref:System.Windows.Forms.Control.BeginInvoke%2A>.</span></span> <span data-ttu-id="0c881-125">`DirectorySearcher` também define um delegado de evento terá o marshaling realizado quando a pesquisa for concluída.</span><span class="sxs-lookup"><span data-stu-id="0c881-125">`DirectorySearcher` also defines an event delegate that is marshaled when the search is completed.</span></span>  
  
```vb  
Option Strict  
Option Explicit  
  
Imports System  
Imports System.IO  
Imports System.Threading  
Imports System.Windows.Forms  
  
Namespace Microsoft.Samples.DirectorySearcher  
   ' <summary>  
   '      This class is a Windows Forms control that implements a simple directory searcher.  
   '      You provide, through code, a search string and it will search directories on  
   '      a background thread, populating its list box with matches.  
   ' </summary>  
   Public Class DirectorySearcher  
      Inherits Control  
      ' Define a special delegate that handles marshaling  
      ' lists of file names from the background directory search  
      ' thread to the thread that contains the list box.  
      Delegate Sub FileListDelegate(files() As String, startIndex As Integer, count As Integer)  
  
      Private _listBox As ListBox  
      Private _searchCriteria As String  
      Private _searching As Boolean  
      Private _deferSearch As Boolean  
      Private _searchThread As Thread  
      Private _fileListDelegate As FileListDelegate  
      Private _onSearchComplete As EventHandler  
  
      Public Sub New()  
         _listBox = New ListBox()  
         _listBox.Dock = DockStyle.Fill  
  
         Controls.Add(_listBox)  
  
         _fileListDelegate = New FileListDelegate(AddressOf AddFiles)  
         _onSearchComplete = New EventHandler(AddressOf OnSearchComplete)  
      End Sub  
  
      Public Property SearchCriteria() As String  
         Get  
            Return _searchCriteria  
         End Get  
         Set  
            ' If currently searching, abort  
            ' the search and restart it after  
            ' setting the new criteria.  
            '  
            Dim wasSearching As Boolean = Searching  
  
            If wasSearching Then  
               StopSearch()  
            End If  
  
            _listBox.Items.Clear()  
            _searchCriteria = value  
  
            If wasSearching Then  
               BeginSearch()  
            End If  
         End Set  
      End Property  
  
      Public ReadOnly Property Searching() As Boolean  
         Get  
            Return _searching  
         End Get  
      End Property  
  
      Public Event SearchComplete As EventHandler  
  
      ' <summary>  
      ' This method is called from the background thread.  It is called through  
      ' a BeginInvoke call so that it is always marshaled to the thread that  
      ' owns the list box control.  
      ' </summary>  
      ' <param name="files"></param>  
      ' <param name="startIndex"></param>  
      ' <param name="count"></param>  
      Private Sub AddFiles(files() As String, startIndex As Integer, count As Integer)  
         While count > 0  
            count -= 1  
            _listBox.Items.Add(files((startIndex + count)))  
         End While  
      End Sub  
  
      Public Sub BeginSearch()  
         ' Create the search thread, which   
         ' will begin the search.  
         ' If already searching, do nothing.  
         '  
         If Searching Then  
            Return  
         End If  
  
         ' Start the search if the handle has  
         ' been created. Otherwise, defer it until the  
         ' handle has been created.  
         If IsHandleCreated Then  
            _searchThread = New Thread(New ThreadStart(AddressOf ThreadProcedure))  
            _searching = True  
            _searchThread.Start()  
         Else  
            _deferSearch = True  
         End If  
      End Sub  
  
      Protected Overrides Sub OnHandleDestroyed(e As EventArgs)  
         ' If the handle is being destroyed and you are not  
         ' recreating it, then abort the search.  
         If Not RecreatingHandle Then  
            StopSearch()  
         End If  
         MyBase.OnHandleDestroyed(e)  
      End Sub  
  
      Protected Overrides Sub OnHandleCreated(e As EventArgs)  
         MyBase.OnHandleCreated(e)  
         If _deferSearch Then  
            _deferSearch = False  
            BeginSearch()  
         End If  
      End Sub  
  
      ' <summary>  
      ' This method is called by the background thread when it has  
      ' finished the search.  
      ' </summary>  
      ' <param name="sender"></param>  
      ' <param name="e"></param>  
      Private Sub OnSearchComplete(sender As Object, e As EventArgs)  
         RaiseEvent SearchComplete(sender, e)  
      End Sub  
  
      Public Sub StopSearch()  
         If Not _searching Then  
            Return  
         End If  
  
         If _searchThread.IsAlive Then  
            _searchThread.Abort()  
            _searchThread.Join()  
         End If  
  
         _searchThread = Nothing  
         _searching = False  
      End Sub  
  
      ' <summary>  
      ' Recurses the given path, adding all files on that path to   
      ' the list box. After it finishes with the files, it  
      ' calls itself once for each directory on the path.  
      ' </summary>  
      ' <param name="searchPath"></param>  
      Private Sub RecurseDirectory(searchPath As String)  
         ' Split searchPath into a directory and a wildcard specification.  
         '  
         Dim directoryPath As String = Path.GetDirectoryName(searchPath)  
         Dim search As String = Path.GetFileName(searchPath)  
  
         ' If a directory or search criteria are not specified, then return.  
         '  
         If directoryPath Is Nothing Or search Is Nothing Then  
            Return  
         End If  
  
         Dim files() As String  
  
         ' File systems like NTFS that have  
         ' access permissions might result in exceptions  
         ' when looking into directories without permission.  
         ' Catch those exceptions and return.  
         Try  
            files = Directory.GetFiles(directoryPath, search)  
         Catch e As UnauthorizedAccessException  
            Return  
         Catch e As DirectoryNotFoundException  
            Return  
         End Try  
  
         ' Perform a BeginInvoke call to the list box  
         ' in order to marshal to the correct thread. It is not  
         ' very efficient to perform this marshal once for every  
         ' file, so batch up multiple file calls into one  
         ' marshal invocation.  
         Dim startingIndex As Integer = 0  
         While startingIndex < files.Length  
            ' Batch up 20 files at once, unless at the  
            ' end.  
            '  
            Dim count As Integer = 20  
            If count + startingIndex >= files.Length Then  
               count = files.Length - startingIndex  
            End If  
            ' Begin the cross-thread call. Because you are passing  
            ' immutable objects into this invoke method, you do not have to  
            ' wait for it to finish. If these were complex objects, you would  
            ' have to either create new instances of them or   
            ' wait for the thread to process this invoke before modifying  
            ' the objects.  
            Dim r As IAsyncResult = BeginInvoke(_fileListDelegate, New Object() {files, startingIndex, count})  
            startingIndex += count  
         End While  
         ' Now that you have finished the files in this directory, recurse  
         ' for each subdirectory.  
         Dim directories As String() = Directory.GetDirectories(directoryPath)  
         Dim d As String  
         For Each d In  directories  
            RecurseDirectory(Path.Combine(d, search))  
         Next d  
      End Sub  
  
      '/ <summary>  
      '/ This is the actual thread procedure. This method runs in a background  
      '/ thread to scan directories. When finished, it simply exits.  
      '/ </summary>  
      Private Sub ThreadProcedure()  
         ' Get the search string. Individual   
         ' field assigns are atomic in .NET, so you do not  
         ' need to use any thread synchronization to grab  
         ' the string value here.  
         Try  
            Dim localSearch As String = SearchCriteria  
  
            ' Now, search the file system.  
            '  
            RecurseDirectory(localSearch)  
         Finally  
            ' You are done with the search, so update.  
            '  
            _searching = False  
  
            ' Raise an event that notifies the user that  
            ' the search has terminated.    
            ' You do not have to do this through a marshaled call, but  
            ' marshaling is recommended for the following reason:  
            ' Users of this control do not know that it is  
            ' multithreaded, so they expect its events to   
            ' come back on the same thread as the control.  
            BeginInvoke(_onSearchComplete, New Object() {Me, EventArgs.Empty})  
         End Try  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace Microsoft.Samples.DirectorySearcher  
{  
   using System;  
   using System.IO;  
   using System.Threading;  
   using System.Windows.Forms;  
  
   /// <summary>  
   ///      This class is a Windows Forms control that implements a simple directory searcher.  
   ///      You provide, through code, a search string and it will search directories on  
   ///      a background thread, populating its list box with matches.  
   /// </summary>  
   public class DirectorySearcher : Control  
   {  
      // Define a special delegate that handles marshaling  
      // lists of file names from the background directory search  
      // thread to the thread that contains the list box.  
      private delegate void FileListDelegate(string[] files, int startIndex, int count);  
  
      private ListBox listBox;  
      private string  searchCriteria;  
      private bool searching;  
      private bool deferSearch;  
      private Thread searchThread;  
      private FileListDelegate fileListDelegate;  
      private EventHandler onSearchComplete;  
  
      public DirectorySearcher()  
      {  
         listBox = new ListBox();  
         listBox.Dock = DockStyle.Fill;  
  
         Controls.Add(listBox);  
  
         fileListDelegate = new FileListDelegate(AddFiles);  
         onSearchComplete = new EventHandler(OnSearchComplete);  
      }  
  
      public string SearchCriteria   
      {  
         get   
         {  
            return searchCriteria;  
         }  
         set   
         {  
            // If currently searching, abort  
            // the search and restart it after  
            // setting the new criteria.  
            //  
            bool wasSearching = Searching;  
  
            if (wasSearching)  
            {  
               StopSearch();  
            }  
  
            listBox.Items.Clear();  
            searchCriteria = value;  
  
            if (wasSearching)  
            {  
               BeginSearch();  
            }  
         }  
      }  
  
      public bool Searching   
      {  
         get   
         {  
            return searching;  
         }  
      }  
  
      public event EventHandler SearchComplete;  
  
      /// <summary>  
      /// This method is called from the background thread. It is called through  
      /// a BeginInvoke call so that it is always marshaled to the thread that  
      /// owns the list box control.  
      /// </summary>  
      /// <param name="files"></param>  
      /// <param name="startIndex"></param>  
      /// <param name="count"></param>  
      private void AddFiles(string[] files, int startIndex, int count)  
      {  
         while(count-- > 0)  
         {  
            listBox.Items.Add(files[startIndex + count]);  
         }  
      }  
  
      public void BeginSearch()   
      {  
         // Create the search thread, which   
         // will begin the search.  
         // If already searching, do nothing.  
         //  
         if (Searching)  
         {  
            return;  
         }  
  
         // Start the search if the handle has  
         // been created. Otherwise, defer it until the  
         // handle has been created.  
         if (IsHandleCreated)  
         {  
            searchThread = new Thread(new ThreadStart(ThreadProcedure));  
            searching = true;  
            searchThread.Start();  
         }  
         else  
         {  
            deferSearch = true;  
         }  
      }  
  
      protected override void OnHandleDestroyed(EventArgs e)  
      {  
         // If the handle is being destroyed and you are not  
         // recreating it, then abort the search.  
         if (!RecreatingHandle)  
         {  
            StopSearch();  
         }  
         base.OnHandleDestroyed(e);  
      }  
  
      protected override void OnHandleCreated(EventArgs e)   
      {  
         base.OnHandleCreated(e);  
         if (deferSearch)  
         {  
            deferSearch = false;  
            BeginSearch();  
         }  
      }  
  
      /// <summary>  
      /// This method is called by the background thread when it has finished  
      /// the search.  
      /// </summary>  
      /// <param name="sender"></param>  
      /// <param name="e"></param>  
      private void OnSearchComplete(object sender, EventArgs e)  
      {  
         if (SearchComplete != null)  
         {  
            SearchComplete(sender, e);  
         }  
      }  
  
      public void StopSearch()  
      {  
         if (!searching)  
         {  
            return;  
         }  
  
         if (searchThread.IsAlive)  
         {  
            searchThread.Abort();  
            searchThread.Join();  
         }  
  
         searchThread = null;  
         searching = false;  
      }  
  
      /// <summary>  
      /// Recurses the given path, adding all files on that path to   
      /// the list box. After it finishes with the files, it  
      /// calls itself once for each directory on the path.  
      /// </summary>  
      /// <param name="searchPath"></param>  
      private void RecurseDirectory(string searchPath)  
      {  
         // Split searchPath into a directory and a wildcard specification.  
         //  
         string directory = Path.GetDirectoryName(searchPath);  
         string search = Path.GetFileName(searchPath);  
  
         // If a directory or search criteria are not specified, then return.  
         //  
         if (directory == null || search == null)  
         {  
            return;  
         }  
  
         string[] files;  
  
         // File systems like NTFS that have  
         // access permissions might result in exceptions  
         // when looking into directories without permission.  
         // Catch those exceptions and return.  
         try   
         {  
            files = Directory.GetFiles(directory, search);  
         }  
         catch(UnauthorizedAccessException)  
         {  
            return;  
         }  
         catch(DirectoryNotFoundException)  
         {  
            return;  
         }  
  
         // Perform a BeginInvoke call to the list box  
         // in order to marshal to the correct thread. It is not  
         // very efficient to perform this marshal once for every  
         // file, so batch up multiple file calls into one  
         // marshal invocation.  
         int startingIndex = 0;  
  
         while(startingIndex < files.Length)  
         {  
            // Batch up 20 files at once, unless at the  
            // end.  
            //  
            int count = 20;  
            if (count + startingIndex >= files.Length)  
            {  
               count = files.Length - startingIndex;  
            }  
  
            // Begin the cross-thread call. Because you are passing  
            // immutable objects into this invoke method, you do not have to  
            // wait for it to finish. If these were complex objects, you would  
            // have to either create new instances of them or   
            // wait for the thread to process this invoke before modifying  
            // the objects.  
            IAsyncResult r = BeginInvoke(fileListDelegate, new object[] {files, startingIndex, count});  
            startingIndex += count;  
         }  
  
         // Now that you have finished the files in this directory, recurse for  
         // each subdirectory.  
         string[] directories = Directory.GetDirectories(directory);  
         foreach(string d in directories)  
         {  
            RecurseDirectory(Path.Combine(d, search));  
         }  
      }  
  
      /// <summary>  
      /// This is the actual thread procedure. This method runs in a background  
      /// thread to scan directories. When finished, it simply exits.  
      /// </summary>  
      private void ThreadProcedure()  
      {  
         // Get the search string. Individual   
         // field assigns are atomic in .NET, so you do not  
         // need to use any thread synchronization to grab  
         // the string value here.  
         try   
         {  
            string localSearch = SearchCriteria;  
  
            // Now, search the file system.  
            //  
            RecurseDirectory(localSearch);  
         }  
         finally  
         {  
            // You are done with the search, so update.  
            //  
            searching = false;  
  
            // Raise an event that notifies the user that  
            // the search has terminated.    
            // You do not have to do this through a marshaled call, but  
            // marshaling is recommended for the following reason:  
            // Users of this control do not know that it is  
            // multithreaded, so they expect its events to   
            // come back on the same thread as the control.  
            BeginInvoke(onSearchComplete, new object[] {this, EventArgs.Empty});  
         }  
      }  
   }  
}  
```  
  
## <a name="using-the-multithreaded-control-on-a-form"></a><span data-ttu-id="0c881-126">Usando o Controle com Multithread em um Formulário</span><span class="sxs-lookup"><span data-stu-id="0c881-126">Using the Multithreaded Control on a Form</span></span>  
 <span data-ttu-id="0c881-127">A exemplo a seguir mostra como o controle com multithread `DirectorySearcher` pode ser usado em um formulário.</span><span class="sxs-lookup"><span data-stu-id="0c881-127">The following example shows how the multithreaded `DirectorySearcher` control can be used on a form.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports Microsoft.Samples.DirectorySearcher  
Imports System  
Imports System.Drawing  
Imports System.Collections  
Imports System.ComponentModel  
Imports System.Windows.Forms  
Imports System.Data  
  
Namespace SampleUsage  
  
   ' <summary>  
   '      Summary description for Form1.  
   ' </summary>  
   Public Class Form1  
      Inherits System.Windows.Forms.Form  
      Private WithEvents directorySearcher As DirectorySearcher  
      Private searchText As System.Windows.Forms.TextBox  
      Private searchLabel As System.Windows.Forms.Label  
      Private WithEvents searchButton As System.Windows.Forms.Button  
  
      Public Sub New()  
         '  
         ' Required for Windows Forms designer support.  
         '  
         InitializeComponent()  
         '  
         ' Add any constructor code after InitializeComponent call here.  
         '  
      End Sub  
  
      #Region "Windows Form Designer generated code"  
      ' <summary>  
      '      Required method for designer support. Do not modify  
      '      the contents of this method with the code editor.  
      ' </summary>  
      Private Sub InitializeComponent()  
         Me.directorySearcher = New Microsoft.Samples.DirectorySearcher.DirectorySearcher()  
         Me.searchButton = New System.Windows.Forms.Button()  
         Me.searchText = New System.Windows.Forms.TextBox()  
         Me.searchLabel = New System.Windows.Forms.Label()  
         Me.directorySearcher.Anchor = System.Windows.Forms.AnchorStyles.Top Or System.Windows.Forms.AnchorStyles.Bottom Or System.Windows.Forms.AnchorStyles.Left Or System.Windows.Forms.AnchorStyles.Right  
         Me.directorySearcher.Location = New System.Drawing.Point(8, 72)  
         Me.directorySearcher.SearchCriteria = Nothing  
         Me.directorySearcher.Size = New System.Drawing.Size(271, 173)  
         Me.directorySearcher.TabIndex = 2  
         Me.searchButton.Location = New System.Drawing.Point(8, 16)  
         Me.searchButton.Size = New System.Drawing.Size(88, 40)  
         Me.searchButton.TabIndex = 0  
         Me.searchButton.Text = "&Search"  
         Me.searchText.Anchor = System.Windows.Forms.AnchorStyles.Top Or System.Windows.Forms.AnchorStyles.Left Or System.Windows.Forms.AnchorStyles.Right  
         Me.searchText.Location = New System.Drawing.Point(104, 24)  
         Me.searchText.Size = New System.Drawing.Size(175, 20)  
         Me.searchText.TabIndex = 1  
         Me.searchText.Text = "c:\*.cs"  
         Me.searchLabel.ForeColor = System.Drawing.Color.Red  
         Me.searchLabel.Location = New System.Drawing.Point(104, 48)  
         Me.searchLabel.Size = New System.Drawing.Size(176, 16)  
         Me.searchLabel.TabIndex = 3  
         Me.ClientSize = New System.Drawing.Size(291, 264)  
         Me.Controls.AddRange(New System.Windows.Forms.Control() {Me.searchLabel, Me.directorySearcher, Me.searchText, Me.searchButton})  
         Me.Text = "Search Directories"  
      End Sub  
      #End Region  
  
      ' <summary>  
      '    The main entry point for the application.  
      ' </summary>  
      <STAThread()> _  
      Shared Sub Main()  
         Application.Run(New Form1())  
      End Sub  
  
      Private Sub searchButton_Click(sender As Object, e As System.EventArgs) Handles searchButton.Click  
         directorySearcher.SearchCriteria = searchText.Text  
         searchLabel.Text = "Searching..."  
         directorySearcher.BeginSearch()  
      End Sub  
  
      Private Sub directorySearcher_SearchComplete(sender As Object, e As System.EventArgs) Handles directorySearcher.SearchComplete  
         searchLabel.Text = String.Empty  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace SampleUsage  
{  
   using Microsoft.Samples.DirectorySearcher;  
   using System;  
   using System.Drawing;  
   using System.Collections;  
   using System.ComponentModel;  
   using System.Windows.Forms;  
   using System.Data;  
  
   /// <summary>  
   ///      Summary description for Form1.  
   /// </summary>  
   public class Form1 : System.Windows.Forms.Form  
   {  
      private DirectorySearcher directorySearcher;  
      private System.Windows.Forms.TextBox searchText;  
      private System.Windows.Forms.Label searchLabel;  
      private System.Windows.Forms.Button searchButton;  
  
      public Form1()  
      {  
         //  
         // Required for Windows Forms designer support.  
         //  
         InitializeComponent();  
  
         //  
         // Add any constructor code after InitializeComponent call here.  
         //  
      }  
  
      #region Windows Form Designer generated code  
      /// <summary>  
      ///      Required method for designer support. Do not modify  
      ///      the contents of this method with the code editor.  
      /// </summary>  
      private void InitializeComponent()  
      {  
         this.directorySearcher = new Microsoft.Samples.DirectorySearcher.DirectorySearcher();  
         this.searchButton = new System.Windows.Forms.Button();  
         this.searchText = new System.Windows.Forms.TextBox();  
         this.searchLabel = new System.Windows.Forms.Label();  
         this.directorySearcher.Anchor = (((System.Windows.Forms.AnchorStyles.Top | System.Windows.Forms.AnchorStyles.Bottom)   
            | System.Windows.Forms.AnchorStyles.Left)   
            | System.Windows.Forms.AnchorStyles.Right);  
         this.directorySearcher.Location = new System.Drawing.Point(8, 72);  
         this.directorySearcher.SearchCriteria = null;  
         this.directorySearcher.Size = new System.Drawing.Size(271, 173);  
         this.directorySearcher.TabIndex = 2;  
         this.directorySearcher.SearchComplete += new System.EventHandler(this.directorySearcher_SearchComplete);  
         this.searchButton.Location = new System.Drawing.Point(8, 16);  
         this.searchButton.Size = new System.Drawing.Size(88, 40);  
         this.searchButton.TabIndex = 0;  
         this.searchButton.Text = "&Search";  
         this.searchButton.Click += new System.EventHandler(this.searchButton_Click);  
         this.searchText.Anchor = ((System.Windows.Forms.AnchorStyles.Top | System.Windows.Forms.AnchorStyles.Left)   
            | System.Windows.Forms.AnchorStyles.Right);  
         this.searchText.Location = new System.Drawing.Point(104, 24);  
         this.searchText.Size = new System.Drawing.Size(175, 20);  
         this.searchText.TabIndex = 1;  
         this.searchText.Text = "c:\\*.cs";  
         this.searchLabel.ForeColor = System.Drawing.Color.Red;  
         this.searchLabel.Location = new System.Drawing.Point(104, 48);  
         this.searchLabel.Size = new System.Drawing.Size(176, 16);  
         this.searchLabel.TabIndex = 3;  
         this.ClientSize = new System.Drawing.Size(291, 264);  
         this.Controls.AddRange(new System.Windows.Forms.Control[] {this.searchLabel,  
                                                        this.directorySearcher,  
                                                        this.searchText,  
                                                        this.searchButton});  
         this.Text = "Search Directories";  
  
      }  
      #endregion  
  
      /// <summary>  
      ///    The main entry point for the application.  
      /// </summary>  
      [STAThread]  
      static void Main()   
      {  
         Application.Run(new Form1());  
      }  
  
      private void searchButton_Click(object sender, System.EventArgs e)  
      {  
         directorySearcher.SearchCriteria = searchText.Text;  
         searchLabel.Text = "Searching...";  
         directorySearcher.BeginSearch();  
      }  
  
      private void directorySearcher_SearchComplete(object sender, System.EventArgs e)  
      {  
         searchLabel.Text = string.Empty;  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c881-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c881-128">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="0c881-129">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0c881-129">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="0c881-130">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="0c881-130">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
