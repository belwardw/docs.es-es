---
title: ICorDebugProcess::IsOSSuspended (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b65a621541f2b4a800f6b3708a6b257374c5866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended (Método)
Obtiene un valor que indica si el subproceso especificado se ha suspendido porque el depurador detener este proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `threadID`  
 [in] El identificador del subproceso en cuestión.  
  
 `pbSuspended`  
 [out] Un puntero a un valor booleano que es `true` si el subproceso especificado se ha suspendido; de lo contrario *`pbSuspended` es `false`.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el subproceso especificado se ha suspendido porque el depurador detener este proceso, el recuento de suspensiones de Win32 del subproceso especificado se incrementa en uno. La interfaz de usuario (UI) del depurador puede tener en cuenta esta información si muestra el sistema operativo (SO) suspende el recuento del subproceso para el usuario.  
  
 El `IsOSSuspended` método tiene sentido sólo en el contexto de depuración no administrada. Durante la depuración administrada, los subprocesos se forma cooperativa suspendido en lugar de suspendido por el sistema operativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
