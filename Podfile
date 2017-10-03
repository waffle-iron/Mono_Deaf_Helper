platform :osx, '10.11'
inhibit_all_warnings!

def common_pods
    pod 'SnapKit', '~> 4.0.0'
    pod 'SwiftLint', '~> 0.22'
end

def testing_pods
    pod 'Nimble', '~> 7.0'
    pod 'Quick', :git => 'https://github.com/Quick/Quick.git', :branch => 'xcode-9-fix'
end

target 'DeafHelper' do
  use_frameworks!
  common_pods

  target 'DeafHelperTests' do
    inherit! :search_paths
    testing_pods

  end
end

post_install do |installer|
    installer.pods_project.targets.each do |target|
        case target.name
            when 'Nimble', 'Quick'
            swift_version = '3.0'
            else
            swift_version = '4.0'
        end
        target.build_configurations.each do |config|
            config.build_settings['SWIFT_VERSION'] = swift_version
        end
    end
end
