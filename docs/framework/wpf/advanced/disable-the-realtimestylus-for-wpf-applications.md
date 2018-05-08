---
title: Desabilitar o RealTimeStylus para aplicativos WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: ddf4a7f4488f957b2f413d61ad02aa59beba30f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Desabilitar o RealTimeStylus para aplicativos WPF
Windows Presentation Foundation (WPF) tem suporte interno para processamento de entrada de toque do Windows 7. O suporte fornecido por meio de entrada de caneta em tempo real da plataforma tablet como <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, e <xref:System.Windows.UIElement.OnStylusMove%2A> eventos. O Windows 7 também fornece entrada multitoque como mensagens de janela Win32 WM_TOUCH. Essas duas APIs são mutuamente exclusivas no mesmo HWND. A habilitação da entrada por toque por meio da plataforma do tablet (o padrão para aplicativos do WPF) desabilita mensagens WM_TOUCH. Como resultado, para usar WM_TOUCH para receber mensagens de toque de uma janela do WPF, desabilite o suporte a canetas internas no WPF. Isso é aplicável em um cenário como uma janela do WPF hospedando um componente que usa WM_TOUCH.  
  
 Para desabilitar a escuta do WPF à entrada por caneta, remova o suporte a tablet adicionado pela janela do WPF.  
  
## <a name="example"></a>Exemplo  
 O código de exemplo a seguir mostra como remover o suporte da plataforma do tablet padrão usando reflexão.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Interceptando entrada na caneta](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
