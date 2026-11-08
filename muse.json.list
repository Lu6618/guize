console.log("[Muse Auto-Approve] 脚本已启动，正在后台监听审批弹窗...");

function autoApprove() {
    // 1. 尝试展开“审核”面板
    const reviewBtn = Array.from(document.querySelectorAll('button')).find(
        b => b.textContent.includes('审核') && !b.disabled
    );
    if (reviewBtn) reviewBtn.click();

    // 2. 点击“更多允许选项”中的“总是允许此站点”
    const moreBtns = Array.from(document.querySelectorAll('button')).filter(
        b => b.textContent.includes('更多允许选项')
    );
    moreBtns.forEach(btn => {
        btn.click();
        setTimeout(() => {
            const alwaysItem = Array.from(document.querySelectorAll('[role="menuitem"], button, div')).find(
                el => el.textContent.trim() === '总是允许此站点'
            );
            if (alwaysItem) alwaysItem.click();
        }, 120);
    });

    // 3. 兜底点击“允许一次”
    const allowOnceBtns = Array.from(document.querySelectorAll('button')).filter(
        b => b.textContent.trim() === '允许一次' && !b.disabled
    );
    allowOnceBtns.forEach(btn => btn.click());
}

// 每 2 秒扫描并处理一次弹窗
setInterval(autoApprove, 2000);
