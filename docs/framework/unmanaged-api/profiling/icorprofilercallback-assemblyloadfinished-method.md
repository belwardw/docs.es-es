---
title: "ICorProfilerCallback::AssemblyLoadFinished (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af5089603c2044b10061a32c5921b9eeadf86b36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="0bb6a-102">ICorProfilerCallback::AssemblyLoadFinished (Método)</span><span class="sxs-lookup"><span data-stu-id="0bb6a-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="0bb6a-103">Notifica al generador de perfiles que un ensamblado ha terminado de cargarse.</span><span class="sxs-lookup"><span data-stu-id="0bb6a-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb6a-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0bb6a-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bb6a-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0bb6a-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="0bb6a-106">[in] Identifica el ensamblado que se cargó.</span><span class="sxs-lookup"><span data-stu-id="0bb6a-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="0bb6a-107">[in] Un valor HRESULT que indica si el ensamblado terminó de cargarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bb6a-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bb6a-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="0bb6a-108">Remarks</span></span>  
 <span data-ttu-id="0bb6a-109">El valor de `assemblyId` no es válido para una solicitud de información hasta que el `AssemblyLoadFinished` se llama al método.</span><span class="sxs-lookup"><span data-stu-id="0bb6a-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="0bb6a-110">Algunas partes de la carga del ensamblado podrían continuar después de la `AssemblyLoadFinished` devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="0bb6a-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="0bb6a-111">Un valor HRESULT de error en `hrStatus` indica un error.</span><span class="sxs-lookup"><span data-stu-id="0bb6a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="0bb6a-112">Sin embargo, un valor HRESULT correcto en `hrStatus` sólo indica que la primera parte de cargar el ensamblado se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bb6a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bb6a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0bb6a-113">Requirements</span></span>  
 <span data-ttu-id="0bb6a-114">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bb6a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bb6a-115">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0bb6a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0bb6a-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bb6a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bb6a-117">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bb6a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb6a-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="0bb6a-118">See Also</span></span>  
 [<span data-ttu-id="0bb6a-119">ICorProfilerCallback (interfaz)</span><span class="sxs-lookup"><span data-stu-id="0bb6a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)