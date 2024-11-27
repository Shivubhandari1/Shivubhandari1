#include <iostream>
#include <string>
#include <vector>
#include <map>

class WebPage {
private:
    std::string title;
    std::vector<std::string> content; // Simplified representation of HTML content
    std::map<std::string, std::string> meta; // Meta tags like keywords, description
    std::string contactInfo; // Simplified contact info representation

public:
    WebPage(const std::string& t) : title(t) {}

    void addContent(const std::string& c) {
        content.push_back(c);
    }

    void addMeta(const std::string& key, const std::string& value) {
        meta[key] = value;
    }

    void setContactInfo(const std::string& ci) {
        contactInfo = ci;
    }

    void display() {
        std::cout << "<html>\n<head>\n<title>" << title << "</title>\n";
        for (const auto& pair : meta) {
            std::cout << "<meta name=\"" << pair.first << "\" content=\"" << pair.second << "\">\n";
        }
        std::cout << "</head>\n<body>\n";
        for (const auto& line : content) {
            std::cout << line << "\n";
        }
        std::cout << "<div id='contact'>" << contactInfo << "</div>\n";
        std::cout << "</body>\n</html>\n";
    }
};

int main() {
    WebPage astroPage("Astro Protective Services");
    astroPage.addMeta("description", "24/7 Security Solutions");
    astroPage.addMeta("keywords", "security, protective services, 24/7, Astro Protective");

    astroPage.addContent("<h1>Welcome to Astro Protective Services</h1>");
    astroPage.addContent("<p>Your trusted partner in security, available 24/7.</p>");
    astroPage.addContent("<p><strong>Services:</strong> Security Guard Services, Patrol Services, Event Security</p>");

    astroPage.setContactInfo("<p>Contact Us:</p><p>Phone: 510-408-8655</p><p>Email: <a href='mailto:info@astroprotective.com'>info@astroprotective.com</a></p>");

    astroPage.display();
    return 0;
}
