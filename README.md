#include <chrono>
#include <iostream>
#include <string>
#include <vector>
#include "StringData.h"

int linear_search(const std::vector<std::string>& container, const std::string& element) {
    for (int i = 0; i < container.size(); i++) {
        if (container[i] == element) {
            return i + 1;
        }
    }
    return -1;
}
int binary_search(const std::vector<std::string>& container, const std::string& element) {
    int lower = 0;
    int upper = container.size() - 1;

    while (upper >= lower) {
        int middle = (upper + lower) / 2;
        if (container[middle] < element) {
            lower = middle + 1;
        } else if (container[middle] > element) {
            upper = middle - 1;
        } else {
            return middle;
        }
    }
    return -1;
}

int main() {

    auto data = getStringData();

    std::cout << "Testing linear search method to find 'not_here'" << std::endl;
    auto begin_time = std::chrono::system_clock::now();
    std::cout << "Index found: " << linear_search(data, "not_here") << std::endl;
    auto ending_time = std::chrono::system_clock::now();
    std::chrono::duration<double> elapsed = ending_time - begin_time;
    std::cout << "Time to execute method: " << elapsed.count() << " seconds\n" << std::endl;

    std::cout << "Testing binary search method to find 'not_here'" << std::endl;
    begin_time = std::chrono::system_clock::now();
    std::cout << "Index found: " << binary_search(data, "not_here") << std::endl;
    ending_time = std::chrono::system_clock::now();
    elapsed = ending_time - begin_time;
    std::cout << "Time to execute method: " << elapsed.count() << " seconds\n" << std::endl;

    std::cout << "Testing linear search method to find 'mzzzz'" << std::endl;
    begin_time = std::chrono::system_clock::now();
    std::cout << "Index found: " << linear_search(data, "mzzzz") << std::endl;
    ending_time = std::chrono::system_clock::now();
    elapsed = ending_time - begin_time;
    std::cout << "Time to execute method: " << elapsed.count() << " seconds\n" << std::endl;

    std::cout << "Testing binary search method to find 'mzzzz'" << std::endl;
    begin_time = std::chrono::system_clock::now();
    std::cout << "Index found: " << binary_search(data, "mzzzz") << std::endl;
    ending_time = std::chrono::system_clock::now();
    elapsed = ending_time - begin_time;
    std::cout << "Time to execute method: " << elapsed.count() << " seconds\n" << std::endl;

    std::cout << "Testing linear search method to find 'aaaaa'" << std::endl;
    begin_time = std::chrono::system_clock::now();
    std::cout << "Index found: " << linear_search(data, "aaaaa") << std::endl;
    ending_time = std::chrono::system_clock::now();
    elapsed = ending_time - begin_time;
    std::cout << "Time to execute method: " << elapsed.count() << " seconds\n" << std::endl;

    std::cout << "Testing binary search method to find 'aaaaa'" << std::endl;
    begin_time = std::chrono::system_clock::now();
    std::cout << "Index found: " << binary_search(data, "aaaaa") << std::endl;
    ending_time = std::chrono::system_clock::now();
    elapsed = ending_time - begin_time;
    std::cout << "Time to execute method: " << elapsed.count() << " seconds\n" << std::endl;

    return 0;
}


