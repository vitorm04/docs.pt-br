---
title: Hospedando conteúdo Win32
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: c0c62f1999feaf591c512314515f01e83fa12591
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052085"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="4c7e2-102">Hospedando conteúdo Win32 no WPF</span><span class="sxs-lookup"><span data-stu-id="4c7e2-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4c7e2-103">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4c7e2-103">Prerequisites</span></span>

<span data-ttu-id="4c7e2-104">Consulte [interoperação do WPF e do Win32](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="4c7e2-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="4c7e2-105">Um passo a passo do Win32 no Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="4c7e2-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="4c7e2-106">Para reutilizar o conteúdo Win32 dentro de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos, use <xref:System.Windows.Interop.HwndHost> , que é um controle que faz com que os HWNDs pareçam [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="4c7e2-107">Como <xref:System.Windows.Interop.HwndSource> , <xref:System.Windows.Interop.HwndHost> é simples de usar: derivar de <xref:System.Windows.Interop.HwndHost> e implementar `BuildWindowCore` e `DestroyWindowCore` métodos, instanciar sua <xref:System.Windows.Interop.HwndHost> classe derivada e colocá-la dentro de seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="4c7e2-108">Se a lógica do Win32 já estiver empacotada como um controle, a `BuildWindowCore` implementação será pouco mais do que uma chamada para `CreateWindow` .</span><span class="sxs-lookup"><span data-stu-id="4c7e2-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="4c7e2-109">Por exemplo, para criar um controle LISTBOX do Win32 em C++:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

<span data-ttu-id="4c7e2-110">Mas suponha que o código Win32 não seja tão independente?</span><span class="sxs-lookup"><span data-stu-id="4c7e2-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="4c7e2-111">Nesse caso, você pode criar uma caixa de diálogo do Win32 e inserir seu conteúdo em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo maior.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="4c7e2-112">O exemplo mostra isso no Visual Studio e no C++, embora também seja possível fazer isso em um idioma diferente ou na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="4c7e2-113">Comece com uma caixa de diálogo simples, que é compilada em um projeto da DLL do C++.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="4c7e2-114">Em seguida, coloque a caixa de diálogo no aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] maior:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="4c7e2-115">Compilar a DLL como gerenciada ( `/clr` )</span><span class="sxs-lookup"><span data-stu-id="4c7e2-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="4c7e2-116">Transforme a caixa de diálogo em um controle</span><span class="sxs-lookup"><span data-stu-id="4c7e2-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="4c7e2-117">Definir a classe derivada de <xref:System.Windows.Interop.HwndHost> com `BuildWindowCore` `DestroyWindowCore` métodos e</span><span class="sxs-lookup"><span data-stu-id="4c7e2-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="4c7e2-118">Substitua o método `TranslateAccelerator` para manipular as teclas do diálogo</span><span class="sxs-lookup"><span data-stu-id="4c7e2-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="4c7e2-119">Substitua o método `TabInto` para dar suporte à tabulação</span><span class="sxs-lookup"><span data-stu-id="4c7e2-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="4c7e2-120">Substitua o método `OnMnemonic` para dar suporte aos mnemônicos</span><span class="sxs-lookup"><span data-stu-id="4c7e2-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="4c7e2-121">Criar uma instância da <xref:System.Windows.Interop.HwndHost> subclasse e colocá-la no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento à direita</span><span class="sxs-lookup"><span data-stu-id="4c7e2-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="4c7e2-122">Transforme a Caixa de Diálogo em um Controle</span><span class="sxs-lookup"><span data-stu-id="4c7e2-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="4c7e2-123">Você pode transformar uma caixa de diálogo em um HWND filho usando os estilos WS_CHILD e DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="4c7e2-124">Vá para o arquivo de recurso (.rc) no qual a caixa de diálogo está definida e localize o início da definição da caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="4c7e2-125">Altere a segunda linha para:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="4c7e2-126">Essa ação não o empacota totalmente em um controle independente; Você ainda precisa chamar `IsDialogMessage()` para que o Win32 possa processar determinadas mensagens, mas a alteração de controle fornece uma maneira simples de colocar esses controles dentro de outro HWND.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="4c7e2-127">Subclasse HwndHost</span><span class="sxs-lookup"><span data-stu-id="4c7e2-127">Subclass HwndHost</span></span>

<span data-ttu-id="4c7e2-128">Importe os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-128">Import the following namespaces:</span></span>

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

<span data-ttu-id="4c7e2-129">Em seguida, crie uma classe derivada de <xref:System.Windows.Interop.HwndHost> e substitua os `BuildWindowCore` `DestroyWindowCore` métodos e:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

<span data-ttu-id="4c7e2-130">Aqui você vai usar o `CreateDialog` para criar a caixa de diálogo que é, na realidade, um controle.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="4c7e2-131">Como esse é um dos primeiros métodos chamados dentro da DLL, você também deve fazer alguma inicialização padrão do Win32 chamando uma função que você definirá posteriormente, chamada `InitializeGlobals()` :</span><span class="sxs-lookup"><span data-stu-id="4c7e2-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="4c7e2-132">Substitua o método TranslateAccelerator para manipular as teclas do diálogo</span><span class="sxs-lookup"><span data-stu-id="4c7e2-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="4c7e2-133">Se executar este exemplo agora, você obterá um controle de caixa de diálogo que exibe, mas ele ignoraria todo o processamento do teclado que torna uma caixa de diálogo funcional.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="4c7e2-134">Agora, você deve substituir a `TranslateAccelerator` implementação (que vem de `IKeyboardInputSink` uma interface que <xref:System.Windows.Interop.HwndHost> implementa).</span><span class="sxs-lookup"><span data-stu-id="4c7e2-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="4c7e2-135">Esse método é chamado quando o aplicativo recebe WM_KEYDOWN e WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

<span data-ttu-id="4c7e2-136">É muito código de uma vez, então as explicações poderiam ser um pouco mais detalhadas.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="4c7e2-137">Primeiro, o código que usa macros C++ e C++; Você precisa estar ciente de que já existe uma macro chamada `TranslateAccelerator` , que é definida em winuser. h:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="4c7e2-138">Certifique-se de definir um método `TranslateAccelerator` e não um método `TranslateAcceleratorW`.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="4c7e2-139">Da mesma forma, há o winuser.h MSG não gerenciado e o struct `Microsoft::Win32::MSG` gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="4c7e2-140">Você pode desambiguar entre os dois usando o `::` operador C++.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}
```

<span data-ttu-id="4c7e2-141">Os MSGs têm os mesmos dados, mas, às vezes, é mais fácil trabalhar com a definição não gerenciada, portanto, neste exemplo, você poderá definir a rotina de conversão óbvia:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

<span data-ttu-id="4c7e2-142">Voltar para `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-142">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="4c7e2-143">O princípio básico é chamar a função do Win32 `IsDialogMessage` para fazer o máximo de trabalho possível, mas não `IsDialogMessage` tem acesso a nada fora da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-143">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="4c7e2-144">Como uma guia de usuário na caixa de diálogo, quando a tabulação passar do último controle na nossa caixa de diálogo, você precisará definir o foco para a parte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamando `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

<span data-ttu-id="4c7e2-145">Finalmente, chame `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-145">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="4c7e2-146">Mas uma das responsabilidades de um método `TranslateAccelerator` está informando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se você lidou com o pressionamento de teclas ou não.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="4c7e2-147">Se você não lidou com isso, o evento de entrada poderá criar um túnel e uma bolha pelo resto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="4c7e2-148">Aqui, você vai expor uma peculiaridade da manipulação de messange de teclado e da natureza da arquitetura de entrada no Win32.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="4c7e2-149">Infelizmente, `IsDialogMessage` não é retornado de nenhuma forma independentemente de lidar ou não com um determinado pressionamento de tecla.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="4c7e2-150">Ainda pior, ele chamará `DispatchMessage()` nos pressionamentos de teclas que ele não deveria manipular!</span><span class="sxs-lookup"><span data-stu-id="4c7e2-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="4c7e2-151">Assim você terá que fazer engenharia reversa de `IsDialogMessage` e apenas chamá-lo para as teclas que você sabe que ele manipulará:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="4c7e2-152">Substituir o método TabInto para dar suporte à tabulação</span><span class="sxs-lookup"><span data-stu-id="4c7e2-152">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="4c7e2-153">Agora que você implementou `TranslateAccelerator`, um usuário pode tabular dentro da caixa de diálogo caixa e fora dela no aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] maior.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="4c7e2-154">Mas um usuário não pode tabular novamente na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-154">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="4c7e2-155">Para resolver isso, você deve substituir `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-155">To solve that, you override `TabInto`:</span></span>

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

<span data-ttu-id="4c7e2-156">O parâmetro `TraversalRequest` informa se a ação da guia é uma guia ou guia de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="4c7e2-157">Substitua o método OnMnemonic para dar suporte aos mnemônicos</span><span class="sxs-lookup"><span data-stu-id="4c7e2-157">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="4c7e2-158">A manipulação de teclado está quase concluída, mas há uma coisa faltando: os mnemônicos não funcionam.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="4c7e2-159">Se um usuário pressionar alt-F, o foco não pulará para a caixa de edição “Nome:”.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="4c7e2-160">Portanto, você substitui o método `OnMnemonic`:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-160">So, you override the `OnMnemonic` method:</span></span>

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

<span data-ttu-id="4c7e2-161">Por que não chamar `IsDialogMessage` aqui?</span><span class="sxs-lookup"><span data-stu-id="4c7e2-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="4c7e2-162">Você tem o mesmo problema que antes: precisa ser capaz de informar o código [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se seu código manipulou o pressionamento de teclas ou não e `IsDialogMessage` não pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="4c7e2-163">Há também um segundo problema, pois `IsDialogMessage` se recusará a processar o mnemônico se o HWND com o foco não estiver dentro da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="4c7e2-164">Instanciar a classe derivada de HwndHost</span><span class="sxs-lookup"><span data-stu-id="4c7e2-164">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="4c7e2-165">Por fim, agora que todo o suporte de chave e guia está em vigor, você pode colocar seu <xref:System.Windows.Interop.HwndHost> no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo maior.</span><span class="sxs-lookup"><span data-stu-id="4c7e2-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="4c7e2-166">Se o aplicativo principal for escrito no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , a maneira mais fácil de colocá-lo no lugar certo é deixar um elemento vazio <xref:System.Windows.Controls.Border> onde você deseja colocar o <xref:System.Windows.Interop.HwndHost> .</span><span class="sxs-lookup"><span data-stu-id="4c7e2-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="4c7e2-167">Aqui, você cria um <xref:System.Windows.Controls.Border> nome `insertHwndHostHere` :</span><span class="sxs-lookup"><span data-stu-id="4c7e2-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

<span data-ttu-id="4c7e2-168">Então, tudo o que resta é encontrar um bom local na sequência de código para criar uma instância do <xref:System.Windows.Interop.HwndHost> e conectá-lo ao <xref:System.Windows.Controls.Border> .</span><span class="sxs-lookup"><span data-stu-id="4c7e2-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="4c7e2-169">Neste exemplo, você irá colocá-lo dentro do construtor para a <xref:System.Windows.Window> classe derivada:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

<span data-ttu-id="4c7e2-170">O que fornece:</span><span class="sxs-lookup"><span data-stu-id="4c7e2-170">Which gives you:</span></span>

![Captura de tela do aplicativo WPF em execução.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="4c7e2-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c7e2-172">See also</span></span>

- [<span data-ttu-id="4c7e2-173">Interoperação Win32 e WPF</span><span class="sxs-lookup"><span data-stu-id="4c7e2-173">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
