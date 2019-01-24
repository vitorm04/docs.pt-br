---
title: Desabilitar o RealTimeStylus para aplicativos WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 7b97a451c52b72ee1ddcec5c58e1848a0b10fb7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616896"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="13ca2-102">Desabilitar o RealTimeStylus para aplicativos WPF</span><span class="sxs-lookup"><span data-stu-id="13ca2-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="13ca2-103">Windows Presentation Foundation (WPF) tem suporte interno para processar a entrada de toque do Windows 7. O suporte é fornecido por meio da entrada de caneta em tempo real da plataforma do tablet como <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, e <xref:System.Windows.UIElement.OnStylusMove%2A> eventos.</span><span class="sxs-lookup"><span data-stu-id="13ca2-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="13ca2-104">O Windows 7 também fornece entrada multitoque como mensagens de janela Win32 WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="13ca2-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="13ca2-105">Essas duas APIs são mutuamente exclusivas no mesmo HWND.</span><span class="sxs-lookup"><span data-stu-id="13ca2-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="13ca2-106">A habilitação da entrada por toque por meio da plataforma do tablet (o padrão para aplicativos do WPF) desabilita mensagens WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="13ca2-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="13ca2-107">Como resultado, para usar WM_TOUCH para receber mensagens de toque de uma janela do WPF, desabilite o suporte a canetas internas no WPF.</span><span class="sxs-lookup"><span data-stu-id="13ca2-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="13ca2-108">Isso é aplicável em um cenário como uma janela do WPF hospedando um componente que usa WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="13ca2-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="13ca2-109">Para desabilitar a escuta do WPF à entrada por caneta, remova o suporte a tablet adicionado pela janela do WPF.</span><span class="sxs-lookup"><span data-stu-id="13ca2-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ca2-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13ca2-110">Example</span></span>  
 <span data-ttu-id="13ca2-111">O código de exemplo a seguir mostra como remover o suporte da plataforma do tablet padrão usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="13ca2-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
```  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ca2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13ca2-112">See also</span></span>
- [<span data-ttu-id="13ca2-113">Interceptando entrada na caneta</span><span class="sxs-lookup"><span data-stu-id="13ca2-113">Intercepting Input from the Stylus</span></span>](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
