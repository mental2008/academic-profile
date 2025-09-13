<h2 id="news" style="margin: 2px 0px 10px;">Recent News 
  <a href="#" id="view-all-news-link" style="font-size: 14px; font-weight: normal; color: #666; text-decoration: none; margin-left: 10px;">[View All]</a>
</h2>

<div class="news" style="margin-bottom: 20px;">
{% capture recent_news %}
- 08/2025: FlashPS accepted to [ACM EuroSys '26](https://2026.eurosys.org) *(CCF-A, acceptance rate: 79/404=<u>19.6%</u>)*.
- 08/2025: I passed my PhD thesis defense!
- 04/2025: Katz accepted to [USENIX ATC '25](https://www.usenix.org/conference/atc25) *(CCF-A, acceptance rate: 100/634=<u>15.8%</u>)*.
- 12/2024: Prism accepted to [USENIX NSDI '25](https://www.usenix.org/conference/nsdi25) *(CCF-A, acceptance rate: 55/401=<u>13.7%</u>)*.
{% endcapture %}
{{ recent_news | markdownify }}
</div>

<!-- All News Section (Hidden by default) -->
<div id="all-news" style="display: none;">
{% capture all_news %}
- 08/2025: FlashPS accepted to [ACM EuroSys '26](https://2026.eurosys.org) *(CCF-A, acceptance rate: 79/404=<u>19.6%</u>)*.
- 08/2025: I passed my PhD thesis defense!
- 04/2025: Katz accepted to [USENIX ATC '25](https://www.usenix.org/conference/atc25) *(CCF-A, acceptance rate: 100/634=<u>15.8%</u>)*.
- 12/2024: Prism accepted to [USENIX NSDI '25](https://www.usenix.org/conference/nsdi25) *(CCF-A, acceptance rate: 55/401=<u>13.7%</u>)*.
- 04/2023: FGD accepted to [USENIX ATC '23](https://www.usenix.org/conference/atc23) *(CCF-A, acceptance rate: 65/353=<u>18.4%</u>)*.
- 08/2022: One paper accepted to [ACM SoCC '22](https://acmsocc.org/2022/) *(CCF-B, acceptance rate: 38/155=<u>24.5%</u>)*.
- 08/2021: Morphling accepted to [ACM SoCC '21](https://acmsocc.org/2021/) *(CCF-B, acceptance rate: 46/145=<u>31.7%</u>)*.
- 12/2020: I joined Alibaba Group as a Research Intern.
- 08/2020: I started my PhD journey at HKUST!
{% endcapture %}
{{ all_news | markdownify }}
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const viewAllNewsLink = document.getElementById('view-all-news-link');
    const recentNews = document.querySelector('.news');
    const allNews = document.getElementById('all-news');
    const newsTitle = document.querySelector('#news');
    
    // Store original display states and title
    const originalStates = new Map();
    const originalTitle = newsTitle.innerHTML;
    let isShowingAll = false; // Track current state
    
    viewAllNewsLink.addEventListener('click', function(e) {
        e.preventDefault();
        
        if (!isShowingAll) {
            // Show all news and hide other sections
            allNews.style.display = 'block';
            recentNews.style.display = 'none';
            
            // Change the main title and update the link text
            const h2Element = newsTitle;
            const linkElement = h2Element.querySelector('#view-all-news-link');
            const textNode = h2Element.childNodes[0]; // The text node before the link
            textNode.textContent = 'News ';
            linkElement.textContent = '[Show Homepage]';
            
            // Update state
            isShowingAll = true;
            
            // Scroll to the top of the page
            window.scrollTo({ top: 0, behavior: 'smooth' });
            
            // Hide all h2 elements except news and their content
            const allH2s = document.querySelectorAll('h2');
            allH2s.forEach(h2 => {
                if (h2.id !== 'news') {
                    // Store original state
                    originalStates.set(h2, h2.style.display);
                    h2.style.display = 'none';
                    
                    // Hide all following elements until next h2
                    let nextElement = h2.nextElementSibling;
                    while (nextElement && nextElement.tagName !== 'H2') {
                        originalStates.set(nextElement, nextElement.style.display);
                        nextElement.style.display = 'none';
                        nextElement = nextElement.nextElementSibling;
                    }
                }
            });
        } else {
            // Show recent news and restore all sections
            allNews.style.display = 'none';
            recentNews.style.display = 'block';
            
            // Restore the original title and link text
            const h2Element = newsTitle;
            const linkElement = h2Element.querySelector('#view-all-news-link');
            const textNode = h2Element.childNodes[0]; // The text node before the link
            textNode.textContent = 'Recent News ';
            linkElement.textContent = '[View All]';
            
            // Update state
            isShowingAll = false;
            
            // Restore all original states
            originalStates.forEach((originalDisplay, element) => {
                element.style.display = originalDisplay;
            });
            originalStates.clear();
        }
    });
});
</script>
